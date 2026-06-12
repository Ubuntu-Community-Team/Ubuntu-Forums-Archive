---
title: "Dapper Firefox Command-line"
date: 2008-07-31
forum: General Help
---

### Post by Mark Erbaugh on 2008-07-31
Recently, Firefox (v 1.5.0.12eol) in Dapper (i386) has stopped responding to links passed in the command line or when a link is clicked on in say, an email. Firefox is still launched, but the link doesn't show up in the address bar and it doesn't navigate to any page.

I've noticed that if Firefox is already running when I click on a link or enter firefox link from the command line, that link is displayed in a new tab in the existing instance.

---

### Post by LowSky on 2008-07-31
Go to /home/ now hit Ctrl+h and it will show your hidden files. then find your .firefox (or .mozilla) and delete what ever contents are in the folder. Hopefull it should work fine afterwards.

And you should really upgrade to Ubuntu 8.04 to get an up to date version of firefox (v3)

---

### Post by Mark Erbaugh on 2008-08-01
Thanks for the suggestion.  I deleted those files.  When Firefox started it acted like it was a first time run (asked me if I wanted to import settings). However, it still behaves the same:  If I click on a link in an email with FF not running, FF comes up with a blank screen. If I click on a link with FF running, FF opens a new tab showing the desired link.

P.S. As I suspected FF, forgot all my bookmarks and other settings, so as Adam and Jamie say, "Don't try this at home!"

---

### Post by msfraser on 2008-08-17
I've had the same problem after doing an 'apt-get upgrade' recently. I used 'apt-get install firefox=1.5.dfsg+1.5.0.3-0ubuntu3' to downgrade the firefox version, all better now.

---

