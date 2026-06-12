---
title: "Best way to reinstall Ubuntu after I messed up my system"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Gosport on 2009-10-09
(I am reposting this because this catagory is more appropriate)

I need to reinstall Ubuntu. (Blank screen after splash) I would like to save all the work that Picasa has been doing (facial recognition in 3.5 running in Wine that has been running for the last week, and also my user accounts and Firefox settings, etc if possible) 

Should I:

1) Just copy my home folder (using the live CD), wipe out the hard drive, install Ubuntu, then finally replace the new home folder with my backed up home folder?

2) Boot into recovery mode, chose "Drop into Shell Prompt" (I think that was the name) and enter some code like this: "sudo apt-get update" then " [FONT=&quot]sudo apt-get dist-upgrade" (obviously I don't know what I'm doing but I saw this code for upgrading and thought it may work for a reinstall too)

3)  Something else??[/FONT]

---

### Post by Gosport on 2009-10-09
I can't be the only one who has ever messed up their system and had to reload the operating system?

---

### Post by rreese6 on 2009-10-09
Why not explained to us what you did before getting the blank screen.
maybe we can fix what you have.
What I do to see what is happening, is when grub starts I hit ESC to get the menu. then i Press "e" to edit, highlight the kernel line and press "e" again. I go to the end of the line and delete the words "quiet splash --" then hit enter the press "b" to boot.
that way I can see what is going on. and any errors that pop up.
let us know what you see. I suspect it is a video card issue.
also let us know what video card you are using.

---

### Post by Gosport on 2009-10-09
I have an integrated ATI Radeon HD 4200

What happened is that I was logged in as a regular user (not the primary user) and, forgetting this, I started to add a printer. I was prompted for a password but the primary user password was unsuccessful (I think it actually wanted a root password, which I don't have anyway.) Anyway I moved my mouse to the upper right corner and selected my primary user account and the screen went blank and froze up. 

I am using a proprietary video driver, don't know if that had anything to do with it.

I'll try your suggestion and let you know in a sec.

---

### Post by Gosport on 2009-10-09
I made the edits you suggested but it all went by so fast I couldn't catch anything.  I rebooted again and didn't see the list of info again.  Seemed to boot the same as it has been since this all went wrong.

---

### Post by Gosport on 2009-10-09
I tried again, from the beginning, and still couldn't see anthing.  The words "quiet splash" were back again so I deleted them again and hit enter then b and as I said I didn't see anything.

---

### Post by Gosport on 2009-10-09
I also tried to boot to the live CD and the computer seems to ignore it and try to boot from the hard drive.  The CD ramps up later nothing happens and it is already booting to the hard drive anyway.  The BIOS are set to boot to the CD first.

---

### Post by rreese6 on 2009-10-11
The LiveCD should have booted up. check to be sure you have the correct CD in the drive and that the CD rom is set to be the first boot device in BIOS again.
try to boot up in the recovery mode (second selection in Grub Menu)
also using the delete of "quiet spalsh --" as before.
that should bring you to a prompt
at this point you should be brought to menu.
You can try to do the xorg repair. and reboot normally, 
if that doesn't work drop to a root prompt from that same recovery menu
at the prompt you can try to manually start the x-server by typing "
"startx". if it is going to fail, it will go blank for a while, just wait. it will exit with errors on the screen. paste those errors here.
if it works, then all we will need to do is repair your video driver installation.

---

### Post by Mostly.Harmless on 2009-10-12
Your not the only one.

I tend to give my computers meltdowns every month or so using the SPM

---

