---
title: "No Common CD-ROM Found"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by quartzeye on 2009-07-23
Ok.  I cannot install 9.04 server because the CD cannot be detected.

BEFORE YOU SUGGEST A SOLUTION!
I have searched and tried every option I could find in this forum without success.
Live CD doesn't work.
Reburned at 1X and verified MD5 didn't work
Installs in a VM on another machine but not here.
Tried the ALT+F2, modprobe suggestions and received fatal errors every time.
Did an ls on the /dev/cdrom folder on the install CD, showed empty.
Running the most current BIOS already
Tried all the F6 options without success.

Repeated it all with the alternative iso burned at 1x

Already had installed 6.04 and 7.10 previously on this hardware WITHOUT AN ISSUE.

NOW I AM OPEN TO SUGGESTIONS.

What changed in the install?  If it worked before what did they change to break the install.  Don't care why!  Just don't understand why they didn't leave it in as a boot option.  I am a linux newbie but this is not my first trip to the rodeo so I can figure my way around an OS install.  However, this one has me stumped.  Again, I don't have a driver disk for a generic CD-ROM, and it Ubuntu has installed from it before.  The system isn't broke, the installer is.

Hardware:
Athlon 1.333
RAM 1.5BG
HD 30GB

Isn't everything else pretty irrelevant since it USED to work!

UPDATE!
It seems that 8.04.3 installs just fine.  Note to the developers, "If it ain't broke don't fix it."  Maybe a little more regression testing is in order to insure backwards compatibility.  I love the open source community but QA has always been a weak spot.

---

### Post by RJARRRPCGP on 2009-07-23
It's looking like the installer is buggy, too, it just suddenly gave a message about no common CD drives being found, but after going past that message and other prompts, it was successful with the CD test. (see below)

And the normal installer always fails after selecting the language, with an error message claiming an error occurred with the CD, it seems that it's refusing to wait for my SCSI Plextor CD drive, attached to an Adaptec 29160 SCSI card. 

It now for no apparent reason stopped liking my Plextor CD drive and Adaptec 29160 SCSI card. :(


-> And the CD is OK! 

But it still acts like the CD or card was torn out when reading it. LOL.

-> But, interestingly, when I used the option to check the CD, after it seemed to prompt for a CD driver, it actually started scanning and the CD test came back OK! 

-> No file errors with any file, like when I did have a bad burn in the past.


And the installation was fine with the alternate installer! What's going on?

---

