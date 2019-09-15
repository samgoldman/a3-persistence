## HTTP Status Code Scavenger Hunt

https://a3-samgoldman.glitch.me

- The goal of this application is to teach users about a subset of HTTP status codes. They are supposed to use the site to induce 14 different status codes from the 2**, 4**, and 5** groups of errors. When they do, they are given an award for that status code.
- Some challenges I faced:
  - I tried to implement either 100 or 102 and ran into significant roadblocks doing so
  - When I had someone test it out, it became very clear that I needed to protect again HTML injection with the comments
  - I had some issues getting the form notifications when signing up, logging in, and changing passwords to work
  - I found it difficult to use semantic HTML (divs were pretty essential in formatting)
- I chose to use local authentication and lowdb for this project. I used these because they were the easiest. I wanted to focus my time on the other aspects of the project.
- I used the picnic CSS framework. I first picked it because the name fit the theme I had in mind, and kept it because it seemed light and easy to use (and it did fit the theme I wanted).
  - Changes I made include fixing margins on the home page, breaking large words in the comment boxes, aligning everything center (persoanl preference), and adjusting the margins around the X buttons for comments (followed the adjustment guide from the picnic documentation).
- Middleware:
  1. passport: provides local authentication strategy.
  2. body-parser: automatically parses JSON.
  3. compression: compresses responses at the cost of response time. Not necessary, but I wanted to try it out.
  4. morgan: logs all requests and the response codes for them. Helped me track codes being sent.
  5. express-rate-limit: used to rate-limit the home page to enable the 429 error code
  6. express-sanitizer: used to sanitize comments submitted by users to prevent HTML injection
  7. isLoggedIn, isNotLoggedIn (custom): written to make user validation easier. isLoggedIn redirects to '/' if the user is not logged in and isNotLoggedIn redirects to '/home' if they are
  8. length checkers (custom, anonymous functions): written to check the length of the URL, headers, and (for POSTs) the body and if they are above the arbirary limits, send the appropriate error status codes.
  9. error page server (custom, anonymous function): written as final middleware to serve any error pages and award users appropriately.


Login: 
- username=demo; password=password123
- Or create your own account


Note: for the purposes of the requirement to have HTML showing only a user's data, the awards display only shows awards achieved by the logged in user. Additionally, the comments display only puts an 'X' button for removal on a user's own comments.

Screenshots:
![https://i.imgur.com/GbGMtwZ.png](https://i.imgur.com/GbGMtwZ.png)
![https://i.imgur.com/x6ZRMkI.png](https://i.imgur.com/x6ZRMkI.png)
![https://i.imgur.com/4QCGmeV.png](https://i.imgur.com/4QCGmeV.png)


## Technical Achievements
- **Tech Achievement 1**: Used bcrypt to encrypt user passwords
- **Tech Achievement 2**: Wrote several custom middleware
- **Tech Achievement 3**: Created a form for users to make their own custom requests
- **Tech Achievement 4**: When an status code is obtained on the home page, the list of awards auto updates
- **Tech Achievement 5**: For security purposes, automatically redirect any requests over HTTP to be over HTTPS (try it out: http://a3-samgoldman.glitch.me)

## Design/Evaluation Achievements
- **Design Achievement 1**: Used semantic HTML tags for major sections of the page (header, footer, main)
- **Design Achievement 2**: From a design perspective, the auto update of Tech Achievement 4 gives the user instantaneous feedback
