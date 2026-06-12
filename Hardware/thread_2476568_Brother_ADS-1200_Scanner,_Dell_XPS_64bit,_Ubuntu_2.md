---
title: "Brother ADS-1200 Scanner, Dell XPS 64bit, Ubuntu 20.04"
date: 2022-06-29
forum: Hardware
---

### Post by prosayic on 2022-06-29
Cannot get machine to see scanner.   Installed brscan5, but nothing showed up on GUI and didn't recognize scanner.  But it did do the install thing and unpacked stuff; could see it on terminal.  
 Someone in Linux group I crasehd advised to uninstall the Brother driver and just rely on XSane.  But XSane didn't recognize scanner, either.  
Also, there are two "USB" ports on scanner; one is normal USB but other has strange configuration, like flattened, thinner HDMI.  The cable that comes with the scanner fits this.  When I tried my own regular USB cable for the 2d port (both say "USB"), it repeatedly crashed my machine.  (Bought it because folks on Amazon said they were Linux users and it worked fine.)  
Newbie.  Please advise.  Thanks!  
PS  Having problem w. Pantum printer -- only prints after I reboot; others report this as well...

---

### Post by kurt18947 on 2022-07-01
Are you aware of this page?

[https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=ads1200_all](https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=ads1200_all)

I haven't used Brother's .deb files in years, I've had very good luck with Brother's installer script for multi function machines but I doubt that is available for the ADS1200. Brother's Linux support pages used to have a lot of outdated information on them so don't do what they say without thinking/asking first. Most likely just install the .deb file and the scanner will work.

---

### Post by mIk3_08 on 2022-07-03
> **prosayic said:**
> PS  Having problem w. Pantum printer -- only prints after I reboot; others report this as well...

There are links for your Pantum printer here. [Click Here.]("https://ubuntuforums.org/showthread.php?t=2303169") 
[HTML]https://ubuntuforums.org/showthread.php?t=2303169[/HTML]
[Click here]("https://old.pantum.com/global/drive/") for your Pantum printer Regards and cheers. 
[HTML]https://old.pantum.com/global/drive/[/HTML]

---

### Post by prosayic on 2022-07-04
Thank you - the Pantum page linked to above is for wireless.  I'm trying to do this w USB cable. The drivers are installed and I used the "Add" printer function.  But it won't print. Says "pending."  Sometimes if I turn machine off, the file I tried to print will start to print when I reboot, for Libre Office file.  Nothing seems to work w. pdf.

---

### Post by prosayic on 2022-07-04
So trick seems to be to install the Brother .deb file and then open XSane and XSane then recognizes scanner.  Either Brother .deb file OR XSane did not work separately.  Working now.

---

### Post by kurt18947 on 2022-07-04
> **prosayic said:**
> So trick seems to be to install the Brother .deb file and then open XSane and XSane then recognizes scanner.  Either Brother .deb file OR XSane did not work separately.  Working now.

Good to hear it's working. Is the scanner working with the document scanner app? I often use gscan2pdf, I can scan, reorder pages then save as a pdf file. One thing I did find interesting if you care about scanned image file size. I recently bought a MFC-J4535DW multifunction. If I scanned in black & white or grayscale in gscan2pdf, the files were relatively large for their resolution, typically 200 dpi. Files scanned in 24 color were smaller than files scanned in black & white. Presumably there is something odd with file compression. I hadn't noticed this with earlier machines, this might be something to check on.

---

### Post by prosayic on 2022-07-25
So, no, the scanner is not working with the scanner app, only XSane.  
And, you're clairvoyant.  And, as your post here anticipates, the XSane interface does not display option that allows multipage output.   Brother instructions for Linux have an asterisk that says that the multipage output is only available for some builds and offers no workaround.  I'll try the gscan2pdf.

---

