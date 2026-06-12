---
title: "[SOLVED] hotmail works no more"
date: 2008-11-02
forum: General Help
---

### Post by sdowney717 on 2008-11-02
using firefox 3 with No way to enter text for the message box.


Running ie6 with wine does work.

so any fix?

---

### Post by ratmandall on 2008-11-02
> **sdowney717 said:**
> using firefox 3 with No way to enter text for the message box.


Running ie6 with wine does work.

so any fix?

I just checked my hotmail email with firefox 3 and all worked fine.

---

### Post by CoreyB. on 2008-11-02
Do you get the prompt that tells you to upgrade your browser, as though Hotmail thinks you are using an old browser?

---

### Post by CoreyB. on 2008-11-02
I checked on my XP and I don't get the message, but I do get it on Ubuntu 8.10.

---

### Post by sdowney717 on 2008-11-02
"Do you get the prompt that tells you to upgrade your browser, as though Hotmail thinks you are using an old browser?"

yes i do.

this problem first showed up when hotmail changed the appearance and functionality of the site.
I was wondering what it could be. 
The text message box and the little icons above that for modifying the message, are basically greyed out.

---

### Post by Yashiro on 2008-11-02
Disable your browser plugins and try it.

Yeah, it is broken.

---

### Post by cariboo on 2008-11-02
You could also use the User Agent Switcher add on fire firefox and set it to IE7

Jim

---

### Post by mefistofeles666 on 2008-11-02
I'm having the same problem.  i tried the user agen switch, and that didn't make it go away. i guess we have to wait for a better firefox fix or something

---

### Post by mempman on 2008-11-02
> **sdowney717 said:**
> "Do you get the prompt that tells you to upgrade your browser, as though Hotmail thinks you are using an old browser?"

yes i do.

this problem first showed up when hotmail changed the appearance and functionality of the site.
I was wondering what it could be. 
The text message box and the little icons above that for modifying the message, are basically greyed out.

If you are getting that prompt, you should still be able to click on "continue to hotmail anyway" option.

Also, last I check, there were no problems loggin into hotmail with a non-Win OS; however, to sign up for an account, one must have had a win-OS, i.e. Internet Explorer.

---

### Post by sdowney717 on 2008-11-02
Oh, yes I can goto my inbox and read messages, I just cant create any new ones.
The message text box is always grayed out. I can enter the email address.

I have a gmail account and that works just fine.

---

### Post by Yashiro on 2008-11-03
Maybe it's time for Ubuntumail.com

---

### Post by Yashiro on 2008-11-03
Install the User agent switcher addon. Set it as IE7.

Try this. Open MSN.com.
If you're signed in, sign out.
Then, sign in.
Sign out.
Clear your cache.
Close browser.
Open hotmail.com.


You might get to send one mail. But it will stop working at some point. Bad coding, really.

---

### Post by Backupfredi on 2008-11-03
Hello Folks

I think, this is the solution, worked fine for me !

[http://ubuntuforums.org/showpost.php?p=6060869&postcount=9](http://ubuntuforums.org/showpost.php?p=6060869&postcount=9)

Greetings from Vienna ,Austria
Backupfredi

---

### Post by Backupfredi on 2008-11-03
Hello Folks

I think, this is the solution, worked fine for me !

[http://ubuntuforums.org/showpost.php?p=6060869&postcount=9](http://ubuntuforums.org/showpost.php?p=6060869&postcount=9)

Greetings from Vienna ,Austria
Backupfredi

---

### Post by Yashiro on 2008-11-03
Setting general.useragent.vendor to Firefox not Ubuntu does indeed work.

---

### Post by sdowney717 on 2008-11-04
tried it and still it does not work. I suppose it just works for everyone else.
I can not enter any text in the message field. It remains greyed out.
Gmail works fine.

I found out that if I change this setting then restart, the settings revert back to Ubuntu.

So HOW do you make it keep the changes when you change the configuration?

ok, I had to move  mv ~/.mozilla ~/.mozilla.old
This let firefox start over as if freshly installed.
afterwards I had to reimport my bookmarks
from /home/username/.mozilla.old/firefox/vh8p0oex.default/bookmarks.html

---

### Post by Yashiro on 2008-11-04
Disable the Ubuntu browser plugin.

---

### Post by c_vladimir on 2009-01-01
> **Yashiro said:**
> Maybe it's time for Ubuntumail.com
It's a good thing that Microsoft is making the transition-away-from-it easier for users. ie. Hotmail doesn't work properly :)

---

### Post by Circuit Rider on 2009-01-03
[NOT SOLVED]

I am in the process of switching from Windows XP to Ubuntu on all my machines. I am encountering the Hotmail problem, too. I don't mind switching to Gmail or something else, but others in the household are not so happy, especially Mrs. CR. Successful transition to Ubuntu in my house depends on solving this problem.

I know MS has changed its website, so there definitely are problems from that side.

But, I also note that when I installed Ubuntu Intrepid on the new home computer last weekend that Hotmail worked fine until Ubuntu downloaded updates. After updates were installed Hotmail would no longer work. Same is true on my laptop, where I installed Hardy in October. Hotmail worked great for a few weeks and after one of the routine updates it didn't.

I tried all the fixes I've seen on the forums to no avail. Useragent changes, etc. None work for me.

So I decided to boot the computer from the CD and go to Hotmail, and it works. CD does not have updates. So I can make Mrs. CR momentarily content by letting her receive and send emails, but this is not a good permanent fix.

While MS is partly to blame, I think there is something in one of those updates -- either Firefox or Ubuntu -- that has changed the way Ubuntu looks to an already not-so-friendly MS website. I am too new to all this to be able to figure out where it is, but I am sure it is there.

Thanks for all your collective input. I love Ubuntu and want to make it work at home, on laptop, and at the office. I would love to get past this glitch.

---

### Post by c_vladimir on 2009-01-06
> **Circuit Rider said:**
> I don't mind switching to Gmail or something else [..]
gMail has **free** services, like POP access, etc. Hotmail does not, for regular users.

---

### Post by Yashiro on 2009-01-06
Hotmail works here.

If it doesn't work for you:
1) You've not followed the user agent changes properly.
2) You are running plug ins that affect your connectivity.

_Problem 1_
In the Firefox address bar, enter in:
```
about:config
```

open about:config in the address bar. Search the list for general.useragent.
Change whatever values you have set to the following:
```

general.useragent.extra.firefox  Firefox/3.0.5
general.useragent.vendor  Firefox
```

Also check
```
network.http.redirection-limit
```
is at least set to the default value of 20.

_Problem 2_
Disable all plugins.

'Noscript' blocking redirects causes hotmail to fail unless you have white listed all of the domains they use.
Blocking any cookies produced via hotmail login can also cause failure.

[I]live.com
microsoft.com
msn.com
passport.com
passport.net[/I]

---

