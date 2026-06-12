---
title: "Can I flash the bios on a Gigabyte GA-F2A88XM-D3H mobo through linux?"
date: 2015-02-21
forum: Hardware
---

### Post by thane1 on 2015-02-21
Having problems flashing the bios.  Downloaded the latest (A88XMD3H.F7) version 7 bios update and tried to flash the bios using the built in Qflash utility in the bios setup page on boot.  Got an error msg that the flash utility program itself needs to be updated to flash the new bios into the system.  After some searching I found that I need to install the version 4 bios file first during which time the utility will also be updated.  Version 4 however is a win .exe file (mb_bios_ga-f2a88xm-d3h_f4.exe)  I have Win 8.1 on this computer, but it runs inside virtualbox.  So I have been trying to make a bootable usb stick with no luck (when I get to the bootsect.exe /nt60 d: line, I get and access denied msg and even adding /force won't help.)  My vers 7 update file is 8.4MB in size.  So I don't think I can make a floppy image on a cd or dvd as I saw suggested on one site.  Also I think I saw somewhere that the flash drive if its a usb stick needs to be formatted as fat32 but not ntfs.  Could be wrong on that though.  Don't know where to go from here.

---

### Post by weatherman2 on 2015-02-21
Yes, I think you will want to use FAT32 format for the flash drive when trying to update the BIOS.

I wonder if you can run that older BIOS exe file in virtualbox/Windows 8.1 just to extract the binary file(s)?  Then put the binary files on a FAT32 flash drive and try updating using Qflash again?  Can you find extracted files that look comparable to the latest BIOS? (the F7 file file maybe?)  Gigabyte probably has official forums where you can post a question like that and someone can give you the safe answer.

Otherwise, the safest thing to do is to do a real Windows install then flash the BIOS in that (even XP would probably work if you have an XP disc laying around or something).  If you have a spare hard drive, that's what I'd do, even if it is a bit time consuming.  You can download legit Windows 7 install media from Digitalriver (will need a product key otherwise will work as a trial for only 30 days, obviously plenty to flash the BIOS).  I understand not everyone has a spare hard drive sitting around, but in cases like this it is handy to have one.

---

### Post by thane1 on 2015-02-21
I'll follow up on your suggestions weatherman2.  I do have a bunch of old hdd's around.  Didn't think of that.  I'll also try the file extraction on my win 8.1 in virtualbox.  I considered trying to do something in vbox, but then thought the 8.1 wouldn't have access to anything on the system outside of that particular vm.  Will report back, when I have more.  I do have another machine which runs on another copy of 8.1 and i tried making a win bootable usb stick on that machine.  But there's something wonky going on when I try to put the system on the stick.  I'll also try your suggestion of a downloadable iso.

---

### Post by weatherman2 on 2015-02-21
No, I wouldn't attempt to update the BIOS itself using Virtualbox - I'd only use it to extract the binary file.  Nor would I try using any non-installation copy of Windows (not a bootable USB or CD) - too dangerous to me, unless this motherboard has a known "failsafe" way to recover a BIOS in case of a bad flash (some of them do).  The safest approach - but the most time consuming - is to install a dummy copy of Windows on a spare hard drive, update the BIOS, and then be done with it.

---

### Post by thane1 on 2015-02-21
Many thanks for the time spent with this problem.  In the interim I did separate the version 4 bios update files in vbox, copied the specific v4 bios file onto a fat32 formatted usb stick and rebooted hitting "end" key to enter the bios update utility.  In Qflash I attempted to install the v4 update and still got the outdated update utility error msg.  My next attempt was to try the Digitalriver route.  But it stalled when I tried to enter my legitimate win 8.1 key for a win 7 iso.  I then tried to install a win 8.1 update onto a usb stick using my legitimate win key on the machine which uses win 8.1.  That didn't work either, although I didn't try the no-key 30 day approach I must admit. I'm just about out of time for today.  Hopefully tomorrow I'll have time to put one of my old hdd's into the main machine, reformat the drive and install my old XP windows on it (Boo redmond, I hate windows).  Then hopefully I can use the windoze based bios update tool to get back on track.  I'll get back to you weatherman2.  Thanks again.  Long live linux.

---

### Post by weatherman2 on 2015-02-21
You don't need a product key - just download a Windows 7 ISO from DigitalRiver and skip the product key and you'll have 30 days to evaluate it - plenty of time to do the BIOS update at first boot.

---

### Post by thane1 on 2015-02-22
Disconnected my hdds in the main linux box and connected an old drive in place.  Deleted partitions and reformatted to ntfs with Knoppix.  So the main box is ready for the win install.  Then on the other (win 8.1) computer went to the Digital River site for the win7 iso.  Unfortunately it seems they no longer have it and gave a link to the MS site.  Went there and tried to download a copy.  But they won't let me dl win 7, 8 or 8.1 without a key.  So I tried the legal key from my win 8.1 which is actually installed on that machine and ms won't even accept that.  So it seems for the time being, until I can get an iso, I'm out of ideas.  I'll look into the possibility of gigabyte forum answers.  But I think your windows install idea would be the best so far.  Thanks again.

---

### Post by weatherman2 on 2015-02-22
Yes, it appears that only recently MS started requiring a product key and took down the old ISO files.  That's a shame.

I'd probably contact Gigabyte support and ask for an opinion.  Maybe there is a BIOS upgrade path (through different versions) you haven't thought of using only QFlash.

---

### Post by thane1 on 2015-02-22
Tried the official gigabyte user forum.  Not much info there.  I'll keep at it.

---

### Post by thane1 on 2015-02-23
Thanks for mentioning the gigabyte forum weatherman2.  I went back and found another post.  I've just updated my bios to version F7.  For those others with Gigabyte GA-F2A88XM-D3H mobos, here's what I needed to do.  The main key is to download the rufus program from rufus.akeo.ie which is a usb thumbdrive formatting tool pretty much set up to format your drive right off the hop.  From the Gigabyte website (I used the U.S. site) download the version F4 and F5 bios .exe packages and also the F7 package or whatever the latest one is at the time of download.  You'll need to get onto a windows box to run the .exe files to decompress them.  The files needed are one efiflash.exe file and the bios files (such as version 4, 5 and 7).  On the win box put your usb drive into the usb2 slot and then run rufus.  It will pop up a formatting options page.  Make sure to select the fat32 option and make your bootable drive.  Really slick.  Mine took some time to format as I used an 8GB thumbdrive.  Once done copy your 3 bios files and the efiflash.exe file onto the thumbdrive.  The forum stated, that you need to get past version 5 of the bios updates to re-enable Q-Flash for later updates.  
Go to your linux box with the Gigabyte mobo, put the thumbdrive into the usb2 slot and press the power button.  When the beep is heard at POST, press the <end> key to jump straight to the boot order options page.  On that page choose the usb option and hit <enter>.  Machine will boot into dos from the thumbdrive.  Type ```
efiflash A88XMD3H.F4
``` and press <enter> (A88XMD3H.F4 was the first bios file to use in my case.)  The F4 bios update will now progress.  Sit back an watch for two or three minutes as efiflash deletes, writes and verifies first the main bios file and then the backup bios file.  When done it will prompt you to exit.  I rebooted into my linux mint just to make sure everything was ok and when satisfied, shut the system down and redid the entire process with the version F5 bios update and efiflash.  Again I checked to make sure I could boot into linux properly and then shut down the linux machine again.  Now you're homefree.  Again with the fat32 bootable drive (which still has the A88XMD3H.F7 file on it) in the usb slot, turn on the machine.  Press F12 once you hear the POST beep and this time the Q-Flash utility will pop up on screen with your newest bios file listed ready to install.  Highlight and press <enter> and your bios will be updated to the latest version.  No more need to boot into dos for bios updates.  By the way you could press <del> at POST to enter the bios options utility and then cursor over to Q-Flash to do the same thing.  But its quicker to just use F12.

---

### Post by weatherman2 on 2015-02-23
What a pain!  Glad you finally got it figured out.

---

### Post by thane1 on 2015-02-24
Aggravating to be sure but a learning process.  Hopefully Gigabyte develops some sort of cross platform update program for Q-Flash in the future.  cheers

---

