---
title: "Gigabyte mobo requires windows to flash BIOS"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by fatsheep on 2007-07-20
From the manual for my [Gigabyte GA-P35-DS3R Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128050):

>  With Q-Flash** you can update the system BIOS without having to enter operating systems like MS-DOS or Windows first.**  Embedded in the BIOS, the Q-Flash tool frees you from the hassles of going through complicated BIOS flashing process.

I thought the section that I have put in bold face above meant that I would not have to make use of any special operating system utilities in order to update the BIOS (I could just put the update file on the floppy drive and update.  Unfortunately, Gigabyte packages their BIOS update in .exe files.  So I ended up booting up Windows XP in order to extract the BIOS update files from the .exe.  This is not the [first post about this issue](http://ubuntuforums.org/showthread.php?t=120952) but I felt this issue deserved a new topic as that one is quite old. 

I am contacting Gigabyte about this issue.  I just thought I should inform everyone of the problem, especially the Gigabyte motherboard users here.

---

### Post by gasnmyveins on 2007-07-20
I have to update mine to see the whole 320 gig drive, but I am running the Feisty Fawn live cd with no windows on the disc. 
 Is there any way I can update my gigabyte GA-7dxr, so it can see the entire drive? Thanks.

---

### Post by fatsheep on 2007-07-21
Check this out:

> Oh I didn't realize the .exe file was a winrar self extracting archive. I also misread the manual instructions, my apologies for that... However, I do not see why this needs to be packaged in a .exe format. I am an Ubuntu Linux user and it would have been much more convenient to me (and probably for gigabyte as well) to download the file in a friendlier format such as a .zip or .rar archive. These formats can be extracted on just about any platform.

Thank you for your time,

- Jesse 'fatsheep' Cambon

**Gigabyte's responce:**

> Hello,

The reason we package the files is because they will not get transfered correctly and most of ISPs and security antivirus programs will not allow them to go through.

thanks.

Way to totally ignore the question! :confused:

I responded:

> I understand that.  I have no problem with packaging the file.  However, I think it would be easier for everyone to use a friendlier package format such as a plain .zip archive.  This archive would be able to extracted easily on just about any platform.  A winrar self extracting format requires a Windows environment.  Also, when a user on a Linux or Mac platform downloads the file, it appears to be an ordinary .exe Windows executable instead of an archive.  This can be quite confusing.  

- Jesse "fatsheep" Cambon

And I await a responce.  


> **gasnmyveins said:**
> I have to update mine to see the whole 320 gig drive, but I am running the Feisty Fawn live cd with no windows on the disc. 
 Is there any way I can update my gigabyte GA-7dxr, so it can see the entire drive? Thanks.

Yep I think this problem has been corrected in the F9 BIOS update for your board: [Here is the link to the BIOS page for your motherboard](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ClassValue=Motherboard&ProductID=1302&ProductName=GA-7DXR).  Just download the latest BIOS update, unpack it with unrar like so:

```
unrar e <FILENAME>
```

Sample output:

```
fatsheep:~/Desktop$ **unrar e motherboard_bios_ga-7dxr_f10.exe **

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal


Extracting from motherboard_bios_ga-7dxr_f10.exe

Extracting  autoexec.bat                                              OK 
Extracting  7DXR.F10                                                  OK 
Extracting  flash867.exe                                              OK 
All OK
```

Now copy these three files to a floppy disk or USB drive and then run Q-flash (on my motherboard I press the end key when the big Gigabyte splash screen displays on boot up to access Q-flash).  The rest should be fairly straight forward.

---

### Post by gasnmyveins on 2007-07-21
The more I try to do things with my computer, the more I'm finding out that I know just about exactly nothing. Thanks for the reply and instructions. Unfortunately, I don't understand most of it. I'll learn, given time, but for now I'm sort of up the creek. Soooooooooo........
 I found an old 4 gig drive and loaded XP on it. Lol, 3 gigs used for the OS and 1 left for storage. Subtract the gig or so needed for the swap file and it starts to look pretty funny. Still, it should work well enough to update my bios. 
 I know this isn't a windows forum, but if I can get some help running the big drive, then I can run Ubuntu on part of it and learn a thing or two. Maybe even figure it out well enough to use it as my promary OS one day. We'll see. First, though, can you tell me how to update the bios in windows. I've downloaded the F10 update. I just need to know what to do with it. Just click it, or is there more to it? Thanks.

---

### Post by fatsheep on 2007-07-24
Got this reply from Gigabyte:

> 
Hello,

Most of our user run Windows, but we apologize for the incovinience.

thanks.

That's what I expected. :(


> **gasnmyveins said:**
> The more I try to do things with my computer, the more I'm finding out that I know just about exactly nothing. Thanks for the reply and instructions. Unfortunately, I don't understand most of it. I'll learn, given time, but for now I'm sort of up the creek. Soooooooooo........
 I found an old 4 gig drive and loaded XP on it. Lol, 3 gigs used for the OS and 1 left for storage. Subtract the gig or so needed for the swap file and it starts to look pretty funny. Still, it should work well enough to update my bios. 
 I know this isn't a windows forum, but if I can get some help running the big drive, then I can run Ubuntu on part of it and learn a thing or two. Maybe even figure it out well enough to use it as my promary OS one day. We'll see. First, though, can you tell me how to update the bios in windows. I've downloaded the F10 update. I just need to know what to do with it. Just click it, or is there more to it? Thanks.

If you are in Windows, you can extract the files from it by double clicking on it (it's a self extracting archive).  To make sure these files don't run off on you, I recommend creating a new folder, putting the .exe file in the folder, and then running the .exe file.  If you are using Linux then you have to open up a terminal, cd to the directory that the .exe file resides in and run the **unrar -e <FILENAME>** command as instructed above.  Obviously replace <FILENAME> with the name of the .exe file.  Remember to include the .exe extension in this filename.  

Now that we have the files extracted, put them on a floppy disk or flash drive.  Now insert the floppy or flash drive that the files are on into the computer and reboot.  Press whatever key you have to press to access the Q-flash utility.  For me it's the END key.  It should be pretty straightforward from there.

---

### Post by fugative on 2007-08-17
Not quite  the same but i'm desperate.
my bios update is HP sp30341.exe and will not open in DOS so  freedos is out.  I have no windows machine.  
any clues

---

### Post by logos34 on 2007-08-17
> **fugative said:**
> Not quite  the same but i'm desperate.
my bios update is HP sp30341.exe and will not open in DOS so  freedos is out.  I have no windows machine.  
any clues

try this:
**[COLOR="Red"][HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")[/COLOR]**

---

### Post by Beaucephus on 2007-08-18
I was able to unpack the BIOS files from the Gigabyte supplied .exe files by using wine.

```
wine nameoffile.exe
```

This will open the self extractor.  The problem I'm having is that my MB is not recognizing the USB drive as advertised for actually flashing the BIOS.:confused:

---

### Post by fugative on 2007-08-18
WOW i really wasn't expecting an answer on this one, I've Googled it till my eyes bled but nothing! 
1st I used the ubuntu way to flash my  xpc which it did famously as i had the .bin and the flash util which ran in DOS, BUT and here's the bump sp30341.exe  (the bios for my zv5000) will ONLY run in a doze environ. HP are pretty linux friendly with their hardware but this is a brick wall.

2nd I'm downing WINE now to try that tack. Wish me luck!!

Thanks guys and any other suggestions welcome JIC

cheers

lappy@lappy:~$ wine sp30341.exe
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\bios\\hr60\\OemFlash.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\bios\\hr60\\OemFlash.exe" failed, status c0000135


OK now i have the files can't find what to use. there is no  .bin or anything familiar. What next?

---

### Post by fatsheep on 2007-08-18
> **fugative said:**
> WOW i really wasn't expecting an answer on this one, I've Googled it till my eyes bled but nothing! 
1st I used the ubuntu way to flash my  xpc which it did famously as i had the .bin and the flash util which ran in DOS, BUT and here's the bump sp30341.exe  (the bios for my zv5000) will ONLY run in a doze environ. HP are pretty linux friendly with their hardware but this is a brick wall.

2nd I'm downing WINE now to try that tack. Wish me luck!!

Thanks guys and any other suggestions welcome JIC

cheers

lappy@lappy:~$ wine sp30341.exe
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\bios\\hr60\\OemFlash.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\bios\\hr60\\OemFlash.exe" failed, status c0000135


OK now i have the files can't find what to use. there is no  .bin or anything familiar. What next?

When you unpack the self extracting .exe file there should be like 3 files.  Put all of them on a floppy disk or USB drive and reboot into Q-Flash.

---

### Post by fugative on 2007-08-18
Thanks but it produces 17 files, trying to cut & paste them all but can't from wine. 
looking into making a doze live cd don't want to throw in the towel  and go to the gates but  can't see many options.

---

### Post by jacob01 on 2007-08-18
> **fatsheep said:**
> From the manual for my [Gigabyte GA-P35-DS3R Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128050):



I thought the section that I have put in bold face above meant that I would not have to make use of any special operating system utilities in order to update the BIOS (I could just put the update file on the floppy drive and update.  Unfortunately, Gigabyte packages their BIOS update in .exe files.  So I ended up booting up Windows XP in order to extract the BIOS update files from the .exe.  This is not the [first post about this issue](http://ubuntuforums.org/showthread.php?t=120952) but I felt this issue deserved a new topic as that one is quite old. 

I am contacting Gigabyte about this issue.  I just thought I should inform everyone of the problem, especially the Gigabyte motherboard users here.

dell does a similare thing withtheir driver downloads. the linux drivers are in an exe file

---

### Post by fatsheep on 2007-08-19
> **fugative said:**
> Thanks but it produces 17 files, trying to cut & paste them all but can't from wine. 
looking into making a doze live cd don't want to throw in the towel  and go to the gates but  can't see many options.

First make sure your .exe file is inside an empty directory.  Then use **unrar e <FILENAME>** to extract the files.  Then put all those files on your USB drive or floppy.  If you still have problems, post the output of that above command and describe what happens when you use Q-Flash. 

Good luck,

- sheep

---

### Post by fugative on 2007-08-27
unfortunately chaps we lost this one the quickest way to up my bios was to partition a 2gb space for doze, load, flash then delete the partition. I then had the problem of MBR but the super grub utility put grub in place again and i was away.. all took a couple of hours.

HP laptop owners let me know if you've found a more ubuntu way about this (not that i'll need it for my zv5000, don't think they'll be updating that anymore) interested to see how not to get put in the spot where you have to do anything but live in a gates free world.



thanks for the help everyone

---

### Post by davidsrsb on 2007-08-27
Reactos could be the long term solution to these problems as it aims to "look like" windows to drivers in a way that wine never can

---

### Post by logos34 on 2007-08-27
> **davidsrsb said:**
> Reactos could be the long term solution to these problems as it aims to "look like" windows to drivers in a way that wine never can

wow, never heard of it till now...had a quick look at the website, sounds promising (I'd even like to support it!) but it appears to have quite a ways to go before it's a viable option.

---

