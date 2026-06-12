---
title: "can't install 8.04 due to function keys won't work"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by tpgames on 2009-06-14
Desktop I got is missing the folder "pool" (due to fool who gave me the desktop). None of the function keys work when I try to install 8.04. "ENTER" works only when I get to the page where you must press F4. I can boot from cd-rom. I do have access to BIOS through the DELETE key. Current version I have installed is 7.10.

I do not know how to wipe the hard drive and am not concerned about losing data. I also don't know if wiping the harddrive would solve this problem so that I can just install from cd. I don't know if the 'pool' folder missing is why functions key won't work.

Keyboard: Belkin, plugged into tower. 
Using AMD. Not sure what else to tell you. 
I am a newbie and broke, so trying to save myself some money. chmod commands I tried, did not work when I tried to copy pool folder into system folder. I'd be happy with a fresh install that overwrites all data if I could do that. 
Thanks for any help I get!

---

### Post by presence1960 on 2009-06-14
did you MD5SUM the iso before you burned it as an image to a CD-R? Here is the link to learn how to MD5SUM : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
here is the link to get the hash to compare your MD5SUM result : [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
your MD5SUM must match the hash exactly or your iso is no good.

If you get an exact match then burn a new disk. Burn it at the slowest possible speed (4x if possible). When you boot off the CD choose "Check CD for defects". If that is ok then choose Install.

Another thing, are you using a USB keyboard? If so you have to go into BIOS and enable support for USB Legacy.

What is the "pool" folder to which you refer?

---

### Post by tpgames on 2009-06-14
The 'pool' folder is a folder in the Ubuntu operations system. It was located on the cd, but not the computer.
However, enabling ubs keyboard was the step I didn't do. I got what I should have gotten now. 

Everything works now, and I see the install screens.  Thanks! 
Now, I get to reinstall all of the programs I want. ;)

---

### Post by presence1960 on 2009-06-14
Glad you got it working...Enjoy Ubuntu.

---

