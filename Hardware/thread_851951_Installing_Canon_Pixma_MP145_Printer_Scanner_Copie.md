---
title: "Installing Canon Pixma MP145 Printer Scanner Copier"
date: 2008-07-07
forum: Hardware
---

### Post by abhilashkumar on 2008-07-07
I saw a lot of posts by people asking how to install the Canon Pixma MP145 in Ubuntu.

This is what worked for me.

I am running 8.04 32bit

1. install Alien using Symaptic Package Manager.

2. Go to [HTTP://www.canon.com](HTTP://www.canon.com), Support and get the 4 required Linux Drivers. **cuijfilter common and cuijfilter MP140 series, scangearmp common and scangearmp 140 series drivers**. Download them to your desktop. **Get the .rpm version only for this to work.**

3. These files are in the .rpm format and they need to be converted to .deb.

4. use the terminal window. cd ~/Desktop. That will put you in the desktop.

5. Convert the files to .deb by using ```
sudo alien --scripts scangearmp-common-1.10-1.i386.rpm
``` and ```
sudo alien --scripts cuijfilter-common-2.80-0.i386.rpm
```. *These are only examples and you need to be exact or it will not work.*

6. Double Click the .deb files and they will be installed. Install the common files first then the 140 series next.

7. Reboot the computer and the scanner will show up in the GIMP Image Editor, File, Acquire, Scangearmp.

8. You then need to go to System, Administration, Printing and configure the MP 145. It is called the MP 140 series and Make and model is a Canon PIXMA MP150 CUPS.

Hope this helps.

---

### Post by s_spiff on 2008-07-21
ok, having issues here. 
1. I'm on a x64 system.
2. Although I installed the .deb's provided on the site, only the printing is working. The scanner shows no response. 
What to do?

---

### Post by abhilashkumar on 2008-07-21
> **s_spiff said:**
> ok, having issues here. 
1. I'm on a x64 system.
2. Although I installed the .deb's provided on the site, only the printing is working. The scanner shows no response. 
What to do?

I am using the 32bit version myself, so I dont know if this is platform specific.

However, you should be able to access the scanner through GIMP. Go to File->Acquire->ScangearMP

Let me know if this works.

Alternatively, I read in the forums that someone had been able to use the scanner using sane (not Xsane).

Cheers.

---

### Post by s_spiff on 2008-07-22
well, i installed even sane, and no change.
As for the option of having Scangear in GIMP, not appearing :(. Any other ideas? as to how to compile the source provided on their site?

---

### Post by abhilashkumar on 2008-07-23
I wont be able to help you if this a x64 thing. I originally started with ubuntu x64 and had to give up and go back to 32. Time for you to hit the forums with renewed zest. :)

By the way... What is your computer configuration? Laptop or Desktop etc.?

You can also try post by @pablosanchezuy in [this thread]("http://ubuntuforums.org/showthread.php?t=841282&highlight=mp145")

---

### Post by itisbasi on 2008-10-31
Didn't have to do anything in intrepid ibex to get the canon mp145 scanner and printer working. I just plugged it in and both were working. I had to struggle to get the scanner working in both gutsy and hardy though.

---

### Post by abhilashkumar on 2009-01-24
> **itisbasi said:**
> Didn't have to do anything in intrepid ibex to get the canon mp145 scanner and printer working. I just plugged it in and both were working. I had to struggle to get the scanner working in both gutsy and hardy though.

I just switched to Linux Mint which is based on Intrepid. The printer works on plugging but not the scanner. Will have to explore.

---

### Post by itisbasi on 2009-04-07
The .deb driver files for canon mp145 printer and scanner are available on the canon india site. 

[http://support-in.canon-asia.com/EN/search?v%3aproject=ASN-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-in.canon-asia.com/EN/search?v%3aproject=ASN-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

I still don't know about the 64 bit driver files though...

---

