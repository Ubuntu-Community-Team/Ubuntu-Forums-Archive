---
title: "[SOLVED] install problem"
date: 2008-11-30
forum: General Help
---

### Post by harshal09 on 2008-11-30
Hi,
I am very new to ubuntu. installed ubuntu for the first time. 
I had vista installed. downloaded ubuntu 8.10 and wubi. both wubi and ubuntu were on the same harddisk, ran wubi which installed ubuntu on drive E:\ 
the installation went fine, after reboot, it asked me for username and password. which i gave. but after that nothing happens. there is a brown background image and the machine hangs. nothing happens.
I tried the terminal thing did a root(hd0,5)
then did setup (hd0)
got:
checking if "boot/grub/stage1" exists ... no
checking if ""grub/stage1" exists ... no
Error 15: File Not Found.
grub>


if i reboot, at this stage, it again asks for the username and password and the brown screen appears the keyboard doesnt work.
please help.

---

### Post by Orlsend on 2008-12-01
This happend to my dad yesterday when he tried upgrading to 8.10 yesterday.

---

### Post by ago on 2008-12-01
[http://ubuntuforums.org/showthread.php?p=6286572#post6286572](http://ubuntuforums.org/showthread.php?p=6286572#post6286572)

---

### Post by Jammanuser on 2008-12-03
> **harshal09 said:**
> Hi,
I am very new to ubuntu. installed ubuntu for the first time. 
I had vista installed. downloaded ubuntu 8.10 and wubi. both wubi and ubuntu were on the same harddisk, ran wubi which installed ubuntu on drive E:\ 



hmm...it could be because wubi installed ubuntu on the E:/ drive instead of on C:/, which is the normal drive that Windows is on... ;)

u could maybe try reinstalling it...and this time make sure that it installs to C:/ drive...:)

Hope my 2 cents helps!

-jammanuser

:D

---

### Post by harshal09 on 2008-12-04
That is correct. wubi did install ubuntu on E:\ as i want to continue using vista with a dual boot ubuntu.
I have tried reinstalling ubuntu on the E:\ again. but with no luck.

> **Jammanuser said:**
> hmm...it could be because wubi installed ubuntu on the E:/ drive instead of on C:/, which is the normal drive that Windows is on... ;)

u could maybe try reinstalling it...and this time make sure that it installs to C:/ drive...:)

Hope my 2 cents helps!

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-04
> **harshal09 said:**
> That is correct. wubi did install ubuntu on E:\ as i want to continue using vista with a dual boot ubuntu.
I have tried reinstalling ubuntu on the E:\ again. but with no luck.

ahh...ok!!! NOW i get it! :D ur one of those people that thinks wubi installs ubuntu on a separate partition...instead of on TOP of Windows, which is what it actually does! like i said above, u should try installing it on C:/ this time, and my guess is u will no longer have that problem! wubi installs just like a regular Windows application...and u can remove it like one too! its the official Windows installer of ubuntu!

See this [SITE]("http://www.wubi-installer.org/") for more details on how wubi works! 
Good luck, and hope this info helps! ;)

Cheers! 

-jammanuser

:D

P.S. once u install wubi **correctly** on the C:/ drive, and it works, u will see that ur computer is dual booted with ubuntu, and that when u reboot, u see a black boot page in which there are **two** boot entries: Windows and ubuntu! Good luck!

---

### Post by harshal09 on 2008-12-04
I have installed wubi on c:\ and used it to install ubuntu on e:\, after the ubuntu was installed successfully i did get the dual boot screen, when i select ubuntu, i am prompted for the username and password. and after that, the screen freezes.
Are u suggesting that i install wubi on c:\ and ubuntu also on c:\? and this will not affect the existing windows?
thanks for all the help.

-Harshal.

> **Jammanuser said:**
> ahh...ok!!! NOW i get it! :D ur one of those people that thinks wubi installs ubuntu on a separate partition...instead of on TOP of Windows, which is what it actually does! like i said above, u should try installing it on C:/ this time, and my guess is u will no longer have that problem! wubi installs just like a regular Windows application...and u can remove it like one too! its the official Windows installer of ubuntu!

See this [SITE]("http:/www.wubi-installer.org") for more details on how wubi works! 
Good luck, and hope this info helps! ;)

Cheers! 

-jammanuser

:D

P.S. once u install wubi **correctly** on the C:/ drive, and it works, u will see that ur computer is dual booted with ubuntu, and that when u reboot, u see a black boot page in which there are **two** boot entries: Windows and ubuntu! Good luck!

---

### Post by Jammanuser on 2008-12-04
> **harshal09 said:**
> so you mean that it won't affect my current windows setup but will install it as an application. this is cool. will give it a try. thanks for the info..
will post back after trying.

yep! that's **exactly** what i mean! :D once u've installed wubi on C:/ drive, come back here, and let me know how it went!

Cheers! ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-04
> **harshal09 said:**
> I have installed wubi on c:\ and used it to install ubuntu on e:\, after the ubuntu was installed successfully i did get the dual boot screen, when i select ubuntu, i am prompted for the username and password. and after that, the screen freezes.
Are u suggesting that i install wubi on c:\ and ubuntu also on c:\? and this will not affect the existing windows?
thanks for all the help.

-Harshal.

wait...HOLD on! i see u modified ur post...

how did u install wubi that quick on C drive? did u mean that u **downloaded** wubi onto C, and then used it to install ubuntu on E? if so, then that makes more sense...

and what i was simply saying is: wubi **installs** ubuntu on the C drive, on TOP of ur Windows OS...the install of wubi and ubuntu isn't separate! when u **install** wubi (that is, RUN it, and so prompt the installation), u start the installation of ubuntu...that's simply what i meant! ;)

Cheers! 

-jammanuser

:D

EDIT: and YES, wubi will not affect ur existing Windows...besides of course the space it will take up on ur hard drive...but other than that, wubi doesn't change Windows! its the same as before after u have installed wubi! Cheers!

---

### Post by Jammanuser on 2008-12-04
whoops...it appears that i typed the wrong link in my above post! ^^^^ i've updated it now, if u want to try clicking on it, to go check out that page! ;)

Cheers! :p

-jammanuser

---

### Post by harshal09 on 2008-12-04
I got the ubuntu 8.10 installable from a friend which i copied to c:\, then i downloaded wubi installable from the wubi website which was around 1 mb, and when after installing wubi, i ran it, it asked me which drive i wanted to install ubuntu, i specified e:\ and it started the installation. 
I think i have done something wrong here.. 
I have read that wubi itself downloads the installable files, but i guess in this case, it has taken the installables which i had copied on c:\.


> **Jammanuser said:**
> wait...HOLD on! i see u modified ur post...

how did u install wubi that quick on C drive? did u mean that u **downloaded** wubi onto C, and then used it to install ubuntu on E? if so, then that makes more sense...

and what i was simply saying is: wubi **installs** ubuntu on the C drive, on TOP of ur Windows OS...the install of wubi and ubuntu isn't separate! when u **install** wubi (that is, RUN it, and so prompt the installation), u start the installation of ubuntu...that's simply what i meant! ;)

Cheers! 

-jammanuser

:D

EDIT: and YES, wubi will not affect ur existing Windows...besides of course the space it will take up on ur hard drive...but other than that, wubi doesn't change Windows! its the same as before after u have installed wubi! Cheers!

---

### Post by Jammanuser on 2008-12-04
> **harshal09 said:**
> I got the ubuntu 8.10 installable from a friend which i copied to c:\, then i downloaded wubi installable from the wubi website which was around 1 mb, and when after installing wubi, i ran it, it asked me which drive i wanted to install ubuntu, i specified e:\ and it started the installation. 
I think i have done something wrong here.. 
I have read that wubi itself downloads the installable files, but i guess in this case, it has taken the installables which i had copied on c:\.

ok...starting to make more sense! ;)

so u said u got Ubuntu from a friend, which u copied to the C:/ drive, AFTER which u downloaded wubi...correct? 

yes, u should **not** have done that! wubi **does** download its own Ubuntu installation files...what u **should** have done is simple downloaded wubi, and ran it...and u wouldn't be having this problem right now! but since u **didn't**...i'd say FIRST remove the ubuntu ISO that u got from ur friend...make sure its gone! and then try running wubi again...and this time specify the C drive!

Good luck, and let me know how it goes... ;)

-jammanuser

:D

EDIT: if u don't mind me asking...where did u download from??? i hope it was from [http://www.wubi-installer.org](http://www.wubi-installer.org)...if not, then u might want to try downloading again, this time from that site, just to make sure that the FIRST part of the process is correct! Cheers!

---

### Post by harshal09 on 2008-12-04
ok will do that and will let you know over the weekend.
thanks for all the help Jammanuser!

Regards,
Harshal.

> **Jammanuser said:**
> ok...starting to make more sense! ;)

so u said u got Ubuntu from a friend, which u copied to the C:/ drive, AFTER which u downloaded wubi...correct? 

yes, u should **not** have done that! wubi **does** download its own Ubuntu installation files...what u **should** have done is simple downloaded wubi, and ran it...and u wouldn't be having this problem right now! but since u **didn't**...i'd say FIRST remove the ubuntu ISO that u got from ur friend...make sure its gone! and then try running wubi again...and this time specify the C drive!

Good luck, and let me know how it goes... ;)

-jammanuser

:D

EDIT: if u don't mind me asking...where did u download from??? i hope it was from [http://www.wubi-installer.org](http://www.wubi-installer.org)...if not, then u might want to try downloading again, this time from that site, just to make sure that the FIRST part of the process is correct! Cheers!

---

### Post by Jammanuser on 2008-12-04
In case u had trouble understanding my above and other posts...here's a **complete** lists of the steps u have to go through in order to get ur Wubi install of Ubuntu up and running:

[INDENT]**1.** Download Wubi installer from [http://www.wubi-installer.org](http://www.wubi-installer.org) (if u have not already done so, of course!)
**2.** Run wubi.exe (of just "wubi" in the case of Windows Vista, which can be found in ur "Downloads" folder)
**3.** Once Wubi has been run, u will be asked to choose a password and username for ur Ubuntu OS. Do so, and then hit either "Next" or "Ok"...i don't remember which one it was!
**4.** Now u can either sit in front of ur computer the whole time while Wubi is installing Ubuntu 8.10...or u can go do something, and come back in about 15 minutes! it should be completed by then...
**5.** Next reboot ur computer, and once ur computer has got past the brand logo (in my case it was the Dell startup page), u will then see a black screen with two entries on it. One is Windows, and the other one is...tada! Ubuntu, of course! Choose this option, and u should be able to boot into Ubuntu fine! Congratulations!!! u just successfully installed Ubuntu 8.10 as a dual boot using Wubi! :D[/INDENT]

Hope this info helps!

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-04
> **harshal09 said:**
> ok will do that and will let you know over the weekend.
thanks for all the help Jammanuser!

Regards,
Harshal.

No problem!! i'm glad i could be of assistance! ;)

And now i'm off to bed...

Cheers! :D

-jammanuser

---

### Post by falcon61102 on 2008-12-04
It sounds to me that you got the dual-boot working and that you have a simple graphics issue to be resolved in your Ubuntu installation.  If you haven't done so, I recommend you check out post 3 that ago posted.

If you start up the computer and get the GRUB which allows you to select which OS you wan and you select Ubuntu, and then login.  That is completely seperate and has nothing to do with your wubi install.  You are running Ubuntu and it seems that Ubuntu has an issue with your graphics chip.  The link that ago provided has a work around/fix that will get you going.

---

### Post by Jammanuser on 2008-12-04
> **falcon61102 said:**
> It sounds to me that you got the dual-boot working and that you have a simple graphics issue to be resolved in your Ubuntu installation.  If you haven't done so, I recommend you check out post 3 that ago posted.

If you start up the computer and get the GRUB which allows you to select which OS you wan and you select Ubuntu, and then login.  That is completely seperate and has nothing to do with your wubi install.  You are running Ubuntu and it seems that Ubuntu has an issue with your graphics chip.  The link that ago provided has a work around/fix that will get you going.

uhh...falcon61102???? in this particular instance, its not a "simple graphics issue" that's his problem! he installed wubi on the wrong drive! :) even if he did what ago suggested, wubi still wouldn't work, because Wubi wouldn't be on TOP of his Windows OS!!! ;)

Cheers! :D

-jammanuser

EDIT: Try not to confuse someone who has almost got his problem fixed...with incomplete or possibly inaccurate information! that's just counter-productive...

---

### Post by harshal09 on 2008-12-06
Falcon, you were absolutely right. 
it was indeed a graphics problem. 
Did:
sudo apt-get remove compiz compiz
sudo apt-get remove compiz compiz-core

and restarted the machine. worked like a charm !!

Thanks everyone!!
> **falcon61102 said:**
> It sounds to me that you got the dual-boot working and that you have a simple graphics issue to be resolved in your Ubuntu installation.  If you haven't done so, I recommend you check out post 3 that ago posted.

If you start up the computer and get the GRUB which allows you to select which OS you wan and you select Ubuntu, and then login.  That is completely seperate and has nothing to do with your wubi install.  You are running Ubuntu and it seems that Ubuntu has an issue with your graphics chip.  The link that ago provided has a work around/fix that will get you going.

---

### Post by Jammanuser on 2008-12-06
> **harshal09 said:**
> Falcon, you were absolutely right. 
it was indeed a graphics problem. 
Did:
sudo apt-get remove compiz compiz
sudo apt-get remove compiz compiz-core

and restarted the machine. worked like a charm !!

Thanks everyone!!

Cool...i'm glad u got it working! :D But did u **first** install Wubi on the C drive??? Somehow I have a feeling that u did... ;)

Cheers! :)

-jammanuser

:D

---

### Post by falcon61102 on 2008-12-06
Glad you got it working.

---

