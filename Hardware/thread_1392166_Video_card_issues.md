---
title: "Video card issues"
date: 2010-01-27
forum: Hardware
---

### Post by savaan on 2010-01-27
I'm trying to install the drivers  for an ATI Radeon X300se card. I've found the installer on the ATI site, but when I try to click on it (a .run file), I get an error message saying that the UT coding or something isn't correct. 

I'm trying to update this driver because this is my living room comp and I use the Svideo on my card to plug into my TV to watch movies, etc. 

Any help would be appreciated!

---

### Post by bondmatt on 2010-01-27
Can you post the link to the file you are trying to use?

---

### Post by savaan on 2010-01-27
The file is located here: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English)

I've gone through the install instructions from their site as well. I get this message when trying to use the Terminal:

sh: Can't open ./ati-driver-installer-9.2-x86.x86_64.run

---

### Post by Greenwidth on 2010-01-28
> **savaan said:**
> The file is located here: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English)

I've gone through the install instructions from their site as well. I get this message when trying to use the Terminal:

sh: Can't open ./ati-driver-installer-9.2-x86.x86_64.run

The download on that page is for the 9.3 not 9.2 as in your command, so it would be:

```
sudo sh ./ati-driver-installer-9-3-x86.x86_64.run
```

or type:

```
sudo sh ./ati
``` then hit tab to auto complete. (assuming you don't have any other files that start with ati in the directory)

---

### Post by RRF2525 on 2010-01-28
I ran into this last night while trying to install the NVIDIA (190) driver from the downloaded .run package.  Here's the fix I found for parsing the file on the Ubuntu site:

1.  Navigate to the .run file
2.  Right-click on the file and select "Properties"
3.  Click the "Permissions" tab
4.  Select "Allow executing file as program"
5.  Click "Close" and run the file

Cheers!

---

### Post by savaan on 2010-01-28
I tried both of these methods...only to get the same results :( 

sh: Can't open ./ati-driver-installer-9.3-x86.x86_64.run 	

If I click on it and choose "Run", it creates a folder like "fxg something" then closes. If I click and choose to run in Terminal, it looks like its going to work...Terminal does something, then I see in red lettering something about ATI install, then it goes away and the Terminal window goes back to normal...then nothing. No driver installed or anything :(

---

### Post by Greenwidth on 2010-01-28
> **savaan said:**
> sh: Can't open ./ati-driver-installer-9.3-x86.x86_64.run
Is that copied from the terminal??
If so, it's still not right it's not 9.3 it's 9-3.

Edit:
Sorry, just read you did get it to start from the terminal, no errors at all?

---

### Post by savaan on 2010-01-28
First, I apologize...I'm currently on my office computer here. The system in question is downstairs in my living room and its having some freezing issues so I'm posting the errors from THAT computer up here on MY computer...confusing. 

Opening the terminal and trying the line commands results in the error that I posted. If I just double click the file itself, I get options. I can run in terminal, cancel, display or just run it. If I run in the terminal, I see SOMETHING working...it goes through, asks me for my user password, then puts a lot of dots on the screen before splashing in red something about ATI install...then the whole terminal window closes and thats the end of that. I have nothing in my system that shows any drivers were installed. If I choose the Run button (not in terminal) it opens a window and looks as if its extracting...then a large red message appears on the window saying it doesn't recognize the character type and asks if I wish to retry. 

The video card in question is an ATI Radeon X300se with Svideo out. When I boot the computer, the Svideo works fine. I can see Ubuntu loading, but it only goes to the splash screen. When the desktop comes up, my TV (Svideo) goes black and the only way I can see whats going on is to attach a regular computer monitor to the box

---

