---
title: "Pidgin does not retain account information on Ibex"
date: 2008-11-06
forum: General Help
---

### Post by kitpierce on 2008-11-06
I can open and run Pidgin with no problem.  I input the login information for my IM accounts (Yahoo, MSN, GoogleTalk, and AIM) and they all log in as expected.  But if I close and reopen Pidgin, none of the account information is retained.  I instantly get the Welcome To Pidgin... splash and it prompts me for all of my account information again.  I checked my home folder and there is not a .pidgin folder (don't know if that's the right folder or not...) but even when I created it manually it doesn't help.

I have just did a fresh install of the 8.10 and applied all updates.  Only other customization I have done is to download the Mac4Lin project and run the install script contained within.

---

### Post by kitpierce on 2008-11-06
Figured it out - the folder is .purple instead of .pidgin and for some reason the ownership of that got changed to root.  Resolved it by running > sudo chown <myusername> -R <myuserhomedirectory> and everything works now.

---

