---
title: "Can't install from CDROM on my Dell Inspiron 1000"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by Chetcpo on 2005-12-23
Hello everyone, I did some reading here and I didn't find the info I needed so I thought I would post my question.

I have a 13 month old Dell laptop and the motherboard died two weeks out of warranty.  I bought another Dell motherboard and put it all together and it booted up but I got a bunch of hardware conflict messages and WinXP wasn't stable.  It seems my XP install could tell the PC components had changed and thought Bill Gates was loosing money so it shut it down.  Attempts too reinstall the OS with the Dell provided discs resulted in errors and shutdown.  In a final desperate attempt I reformatted the HD and tried again to no avail.  Which is why I am here.

I downloaded and burned the Ubuntu install disc last night and tried to install it this morning.  I put in the disc, started the laptop and I get the following message:

"NTLDR is missing, press Ctrl+Alt+Del to restart."

Boot menu is set to the following:
1 CD drive
2 USB Disc drive
3 Hard Drive
4 Network
5 diagnostics

So is this do-able or am I going to have to look elsewhere for an OS?

Thanks

---

### Post by Cpt. Charisma on 2005-12-23
You are very brave to be replacing laptop mother boards.  ;)

If you have the boot order set properly, but the machine won't boot off the cd it's most likely a hardware problem. NTLDR is a windows thing, so it looks like your laptop is still trying to boot off the HD. Try checking all the connections again. Does the CDROM drive spin up? Does the little light on it blink? Was it ever able to boot off of a cd?

Also, you may have burned the cd wrong, althought I doubt that someone who can replace the motherboard in his laptop would make this mistake. For everyone else though, it's not enough to make a data cd with the .iso file on it. You have to tell your burning software to burn an "image" then select the file. You will only be able to choose one file, and if you put the cd in the drive under windows or linux, you will see several files and folders instead of one .iso file.

---

### Post by Chetcpo on 2005-12-23
Oh no I'm not brave, just foolhardy.  Here is how the new motherboard was "packaged."  Made install a snap.;) 

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=6827013837&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=6827013837&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1)


I'm pretty sure I burned the correct CD.  When I stick it in my functioning computer it appears as a single file: ubuntu-5.10-install-i386.iso

I guess since I formatted it with the WinXP CD (Dell OEM) it left a Windows image.  Is there a way to do a clean format and try again?

The computer will boot from the WinXP CD but it takes me to "setup" and tries to start an install that it is incapable of finishing. (says it cant find files etc.)

---

### Post by Sef on 2005-12-23
Did you do an md5sum check to make sure it burned right?

---

### Post by fordfan753 on 2005-12-23
[QUOTE=Chetcpo]I'm pretty sure I burned the correct CD.  When I stick it in my functioning computer it appears as a single file: ubuntu-5.10-install-i386.iso[/QUOTE]

This means you must have burnt it as a file, not as an image, by putting it in a working computer you should see a whole lot of files and folders.

---

### Post by Chetcpo on 2005-12-24
Update.  

I didn't burn it right.  I reburned it as an image, should work now but doesn't.

Still says: NTLDR is missing press C,A,D, to restart.:confused:

Is there a way to format the HD again?  I used the XP reinstallation disc to format so it may not be clean of windows.  Is there a way to get DOS booted up and format from there?

---

### Post by kaamos on 2005-12-24
The hd really shouldn't matter.. I think you should be able to boot from cd even **without** a hd. Check the cd in another computer to make shure it's ok. Also tell us some answers to these questions
> 
If you have the boot order set properly, but the machine won't boot off the cd it's most likely a hardware problem. NTLDR is a windows thing, so it looks like your laptop is still trying to boot off the HD. Try checking all the connections again. Does the CDROM drive spin up? Does the little light on it blink? Was it ever able to boot off of a cd?

---

### Post by Chetcpo on 2005-12-24
[QUOTE=kaamos]The hd really shouldn't matter.. I think you should be able to boot from cd even **without** a hd. Check the cd in another computer to make shure it's ok. Also tell us some answers to these questions[/QUOTE]


Try checking all the connections again. Does the CDROM drive spin up? 

No (not with Ubuntu disc, but when I put in a windows disc it stops on bootup and says to hit any key to boot from disc- I don't get that option with the ubuntu disc)


Does the little light on it blink? 

Yes, but then it stops and the HD light does all the blinking.

Was it ever able to boot off of a cd? 

Yes.  The Windows XP reinstall disc (from Dell)

---

### Post by kaamos on 2005-12-24
[QUOTE=Chetcpo]Try checking all the connections again. Does the CDROM drive spin up? 

No (not with Ubuntu disc, but when I put in a windows disc it stops on bootup and says to hit any key to boot from disc- I don't get that option with the ubuntu disc)[/QUOTE]
I suggest burning the cd as an image again and with a very slow burning speed.. As this looks like an issue with the cd. It should not be possible that the machine wants to boot from a windows cd, but not from a linux one. It can't be that evil.. ;)

Some extra info: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

