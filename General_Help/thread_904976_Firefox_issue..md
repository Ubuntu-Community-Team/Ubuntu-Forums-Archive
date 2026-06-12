---
title: "Firefox issue."
date: 2008-08-29
forum: General Help
---

### Post by EmanresuusernamE on 2008-08-29
Can someone help me fix an issue with Firefox?  I'm trying to log into a site, but it won't accept my authentication with Firefox at all.  I enter my username and password, but whenever I click Submit, it just sits there and does nothing.  Konqueror tries to connect, but won't accept anything as a password at all.  The website is: 

[https://control.itsupport247.net/](https://control.itsupport247.net/)

It works fine with IE, and I've tried ies4linux, but since I can't get ActiveX OR Java to work with it, it's useless.  This is one of the final steps for me to convince my boss completely to use Linux over Windows, so any and all help will be appreciated.

Thanks.

---

### Post by Mgiacchetti on 2008-08-29
middle click the submit button

Strange problem but it worked for me, went to the validate.asp

Might be a problem in the code for mozilla portion, install opera, and try it with that, or get an add on for mozilla (user agent switcher) and have it see your browser as ie or whatever, to see if it works that way...  IF so, then have the web master review said portion.

---

### Post by EmanresuusernamE on 2008-08-30
Nope, tried both of those.  I tried user agent switch and it still didn't go through.  It will get to the validation script, but won't do anything afterwords.

Just tried Opera, it doesn't seem to be sending the username and password correctly when I hit submit.  Seems to be something wrong with non-IEs so far.

I need to find a way to get a username and password for testing purposes only.

---

### Post by EmanresuusernamE on 2008-09-22
Ahhh, interesting, I found a bit more info with what's going on with this issue.  Firefox states that "window.event" is undefined on line 218.

```
	var e=window.event.keyCode; 
```
Is it me, or is this bad coding?

---

