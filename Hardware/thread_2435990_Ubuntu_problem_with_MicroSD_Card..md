---
title: "Ubuntu problem with MicroSD Card."
date: 2020-01-29
forum: Hardware
---

### Post by denverdecoy on 2020-01-29
Hello, I am fairly new to Ubuntu and having a problem that I would surly love to fix. My machine is a Lenovo 130s, it's a fairly new budget laptop that I am using for school and learning to code. The machine came with Windows 10 and so far has performed great for all my needs. I decided to add Ubuntu alongside windows 10 so I can get more familiar with Linux and so far I have been very pleased with Ubuntu's performance except for this one issue.

**Problem:** The machine has a micro SD card reader with a Samsung 128GB U3 card inserted. In windows, any files added to the card persist as expected. In Ubuntu, however, anything I add to the card is gone after a reboot.

To be clear, If I add files to the card while booted in windows, they are fine and can be read/used by both OSs, but anything added while I am in the Ubuntu OS, is gone after a reboot, regardless of OS.

Note: Any attempts to Format/Partition the SDcard while in Ubuntu (Using Gparted) are met with all kinds of I/O Errors, Formatting in windows to NTFS works fine without errors.

Thanks for looking!

---

### Post by slickymaster on 2020-01-29
Thread moved to **Hardware** for a better fit

---

### Post by oldfred on 2020-01-29
If NTFS Windows sets hibernation flag if fast start up is on. And Windows keeps turning it on with updates. So any data written from Linux, is removed as it restores from hibernation the file structure.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by coffeecat on 2020-01-29
> **denverdecoy said:**
> 
**Problem:** The machine has a micro SD card reader with a Samsung 128GB U3 card inserted. In windows, any files added to the card persist as expected. In Ubuntu, however, anything I add to the card is gone after a reboot.

To be clear, If I add files to the card while booted in windows, they are fine and can be read/used by both OSs, but anything added while I am in the Ubuntu OS, is gone after a reboot, regardless of OS.

Note: Any attempts to Format/Partition the SDcard while in Ubuntu (Using Gparted) are met with all kinds of I/O Errors, Formatting in windows to NTFS works fine without errors.


Classic symptoms of Windows fast startup needing to be disabled! :)

Windows doesn't close down but enters some sort of franken-sleep-hibernation mode. If it detects changes in filesystems when being started up (in reality awoken) it reverses them. Changes made in Ubuntu are reversed. Changes made in Windows survive a reboot.

Here's how you disable Windows fast startup:

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Disadvantage: Windows takes longer to boot.

Advantage: you get to keep your hair!

**Edit:** ninja'd by oldfred, but you get the picture.

---

### Post by denverdecoy on 2020-01-29
Unfortunately disabling "Fast startup" Has not fixed my problem :(

What I did: I followed the instructions to disable fast startup, did a quick reformat to NTFS. Created a couple of folders and files on the drive while in windows. Restarted machine and went over to Ubuntu, Drive contains windows files and folders. Created a few new files and folders from Ubuntu, went back to windows and they are gone again (Also gone when going back to Ubuntu). I did this whole process twice just in case, Dang I was really hoping this would fix it.

The Card seemingly works perfectly in windows, Could this be a driver issue within Ubuntu?

Thanks again for all the help.

---

### Post by denverdecoy on 2020-01-29
Update: Just as a test I loaded Ubuntu, added some files and folders, un-mounted the drive and remounted, and they are gone. The ones I previously added in windows are still there, this is so frustrating! This machine has a pretty small internal storage so I was kind of counting on this microSD working as my larger volume, what a bummer.

---

### Post by coffeecat on 2020-01-29
After disabling fast startup in Windows, did you reboot at least once into Windows before booting into Ubuntu to add files there?

Also double-check that fast startup is still disabled. Windows may have done something between startups. Unlikely, but your symptoms do describe the fast startup problem.

---

### Post by denverdecoy on 2020-01-29
I tried booting windows again, just to make sure, Fast boot is still disabled. Went back to ubuntu, Files still don't persist even thru a "unmount" and "remount" unfortunately. Only the files created in windows persist. I am guesing this is probably a driver issue since this is a newer machine,  which is unfortunate because Lenovo doesn't offer drivers for Linux :(

---

### Post by coffeecat on 2020-01-29
> **denverdecoy said:**
> I am guesing this is probably a driver issue since this is a newer machine,  which is unfortunate because Lenovo doesn't offer drivers for Linux :(

It is not a driver issue. The ntfs-3g driver that comes as default in Ubuntu is a perfectly capable read-write driver for NTFS.

---

### Post by sudodus on 2020-01-29
Your machine is a Lenovo 130s. I could test with Ubuntu 19.10 in a Lenovo V130, and it can write data that persist to an SD card. The two computers are different, but I think several components are the same.

Which version of Ubuntu are you running?

How do you write the files? Maybe you can try with

```

echo 'Hello World' > hello.txt

```

and test with

```

cat hello.txt

```

before and after unmounting and remounting.

You could also try with another file system (than NTFS). I suggest that you create an ext4 file system (with gparted), and try again with the commands above.

---

### Post by sudodus on 2020-01-29
> **coffeecat said:**
> It is not a driver issue. The ntfs-3g driver that comes as default in Ubuntu is a perfectly capable read-write driver for NTFS.

It seems unlikely, but maybe it is an issue with the driver (or firmware or whatever that software is called) for the USB hardware in the computer or in the pendrive.

---

### Post by denverdecoy on 2020-01-29
I am running Ubuntu 18.04.3 LTS, I will try your suggestion.

Edit: I tried your idea, I created a simple "Hello World" program using golang (the language im learning), went to terminal, ran the program from the terminal with no issue. I un-mounted the disk and re mounted, tried again, got: stat test.go: no such file or directory.

---

### Post by denverdecoy on 2020-01-29
I decided to install Ubuntu 19.10 and still no luck. Files added to the SDCard in Ubuntu are gone after un-mount and re-mount... Any other ideas are welcome...

:(

---

### Post by sudodus on 2020-01-30
Well, you could take one more step in the same direction: try the developing version, which has a newer linux kernel and newer hardware drivers.

The developing version, Focal Fossa, will be released as 20.04 LTS in April. You can download the daily iso file from the following page

[Download links for Ubuntu Desktop amd64 ](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/206962/downloads)

Sometimes you need the newest possible version to run Ubuntu with new hardware.

Edit: By the way, maybe your golang program does not 'finish' writing all the way. Please try with the crude echo command, that I suggested in post #10. After that read with cat before and after unmounting and remounting.

---

### Post by denverdecoy on 2020-01-30
> **sudodus said:**
> Please try with the crude echo command, that I suggested in post #10. After that read with cat before and after unmounting and remounting.

I gave it a shot, after unmounting and remounting I get "cat: hello.txt: No such file or directory"

I don't know if I'm ready to try the most 'bleeding edge' version of Ubuntu, as I need the OS to be stable, I sure do appreciate all the help in the meantime though. Hopfully in the future the problem will resolve :\

---

### Post by sudodus on 2020-01-30
I'm sorry, but I have no more ideas right now. This problem is really strange.

I understand that you do not want to install the most 'bleeding edge' version of Ubuntu. You are right about that.

But you can still test it. **Run Ubuntu live, select 'Try Ubuntu', when booting from the USB install drive** (or DVD disk), and do the same tests as you have done with your installed systems.

---

### Post by denverdecoy on 2020-01-30
> **sudodus said:**
> But you can still test it. **Run Ubuntu live, select 'Try Ubuntu', when booting from the USB install drive** (or DVD disk), and do the same tests as you have done with your installed systems.

This is a great idea and I will give it a shot, thanks again for all the assistance thus far! :)

---

### Post by sudodus on 2020-01-31
I'm looking forward to the result, when you  try the developing version live, 'Try Ubuntu'.

[hr][/hr]
After a good night's sleep I have another idea:

It is also possible that the SD card is damaged, made read-only, 'gridlocked'. The symptoms indicate that this might be the case.

And it is possible that Windows keeps information about what is (should be) written to the drive because it is not really flushing its RAM and or storage for hibernation or semi-hibernation alias 'fast startup'.

In order to check for that, you can test in a second computer with Windows, that things can be written and after that read in yet another computer (or the first computer).

See the following link that describes with more details how to analyze the problem, and if you are lucky, to solve it,

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) - Analysis of the problem

---

### Post by denverdecoy on 2020-02-03
I tried your suggestion, I put the microSD into my only other device with a microSD slot, my phone. The phone (android) immediately complained about the file system and requested a format, which apparently formatted to exfat. I threw some photos on the card, and put it back in the laptop. Ubuntu gives a mount error (Unable to access), despite already having the exfat drivers installed. Switching over to windows, the drive works as expected and the photos I added on my phone are present and accounted for.

I'm really thinking this has to do with drivers regarding the actual laptop sdcard reader.

I sure do appreciate your ideas though! I havn't yet tried a live instance of the 'bleeding edge' Ubuntu, maybe I will try that tonight.

---

### Post by tiger-jrsmit on 2020-02-04
I cannot believe this is the first Hardware thread that comes up!!

This is **definately hardware related**. There is something funny about the SD card that is used by the Lenovo s130. I have tested this accross different kernels and Linux opperating systems. What I noticed is that writing to SD cards does not complete properly when using Linux only! It seems that when performing writes to an ntfs files system it corrupts/registers empty files have been copied (as if the inodes are not updated). However, it is not limited to NTFS. I have had issues accross different FSs. I have noticed that when I format the card using ubuntu it fails due to not being able to 'write super blocks' and while attempting to mount a part of the card as a swap file in a fresh install of ubuntu there is a persistant ''cannot verify signal voltage switch " error when attempting to write to the SD card. The hardware works well under windows, but I noticed that windows does not recognise the reader prior to the driver being installed, it seems there is some strange non-generic characteristic.

---

### Post by denverdecoy on 2020-02-04
> **tiger-jrsmit said:**
> I cannot believe this is the first Hardware thread that comes up!!

This is definately hardware related. There is something funny about the SD card that the Lenovo s130 is using. I have tested this accross different kernels and Linux opperating systems. What I noticed is that writing to SD cards does not complete properly when using Linux only! It seems that when performing writes to an ntfs files system it corrupts/registers empty files have been copied (as if the inodes are not updated). However, it is not limited to NTFS. I have had issues accross different FSs. I have noticed that when I format the card using ubuntu it fails due to not being able to 'write super blocks' and while attempting to mount a part of the card as a swap file in a fresh install of ubuntu there is a persistant ''cannot verify signal voltage switch " error when attempting to write to the SD card. The hardware works well under windows, but I noticed that windows does not recognise the reader prior to the driver being installed, it seems there is some strange non-generic characteristic.

It's nice to know I'm not crazy and someone else has experienced this! Now how to we get this fixed?

Note: I really like Ubuntu, I would honestly like to use ONLY Ubuntu and remove windows 10 altogether, but honestly this one problem is the main thing holding me back. Unfortunately the machine only has a 64gb internal drive, so not being able to use the microSD is really a bummer.

(Thanks for chiming in) :)

---

### Post by sudodus on 2020-02-04
I'm inclined to agree, that this is an issue between some hardware and its linux driver, and that the crucial hardware can be the card reader.

If you can get (maybe borrow) a separate card reader, that connects via USB, you can check if it would work better that way to connect to the microSD card.

---

### Post by Autodave on 2020-02-04
Whenever I see a *super block* error, that tells me that that storage device is history: dead.

---

### Post by denverdecoy on 2020-02-04
> **Autodave said:**
> Whenever I see a *super block* error, that tells me that that storage device is history: dead.

And if that device works perfectly on different OS' like windows and android?

---

### Post by Autodave on 2020-02-05
The last thing that I would try is to format it to NTFS on Linux.  (Not sure if you tried that already or not.)  If you cannot do it on Linux, or if you come up with a super block error again while trying to format it, then I would still be inclined to say that the card is defective.

---

### Post by denverdecoy on 2020-02-05
> **Autodave said:**
> The last thing that I would try is to format it to NTFS on Linux.  (Not sure if you tried that already or not.)  If you cannot do it on Linux, or if you come up with a super block error again while trying to format it, then I would still be inclined to say that the card is defective.

If I try to format/partition while in Ubuntu, I am met with all kinds of errors (though I havn't seen the "superblock" error myself). However, both formatting and transferring files works perfectly on windows, and on my android device, so the card itself being defective seems unlikely to me.

---

### Post by sudodus on 2020-02-05
I still suspect, that this is an issue between some hardware and its linux driver, and that the crucial hardware can be the card reader.

If you can get (maybe borrow) a separate card reader, that connects via USB, you can check if it would work better that way to connect to the microSD card. Or you could try with Ubuntu live (booted from a USB drive) in another computer with different hardware.

---

### Post by mtlinix on 2020-03-12
sd card reader works on my lenovo s130 and latest lubuntu 19.10.
it did not work with previous lubuntu versions i was using.

---

### Post by tiger-jrsmit on 2020-04-01
After some reading it seems to be a kernel regression due to the addition of OCP function support, see [https://bugzilla.kernel.org/show_bug.cgi?id=204003](https://bugzilla.kernel.org/show_bug.cgi?id=204003).
I was able to fix this by loading the driver provided by realtech, see [https://www.realtek.com/en/component/zoo/category/card-reader-solutions-card-reader-controllers-software](https://www.realtek.com/en/component/zoo/category/card-reader-solutions-card-reader-controllers-software)

---

