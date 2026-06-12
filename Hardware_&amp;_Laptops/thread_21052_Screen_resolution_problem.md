---
title: "Screen resolution problem"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by WunderStump on 2005-03-20
Just installed Ubuntu Hoary 5.04 (lovin' it!) but I can't seem to convince it to allow anything other than 640x480. I'm running on a Dell Inspiron 2500 laptop and just don't know how to force it to allow 800x600. Any suggestions would be much appreciated!

This is my first Linux install in a while and, I must say, they've certainly come a long way.

~ 'Stump

---

### Post by WunderStump on 2005-03-20
I answered this myself. I had to add the appropriate HorizSync and VertRefresh values for my chipset. Just FYI, for anyone using an Insprion 2500 with the Intel Corporation 82815 CGC chipset and i810 drivers whose resolution seems locked at 640x480, just make sure your "Monitor" section looks something like this:

```
Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       31-70
        VertRefresh     50-160
        Option          "DPMS"
EndSection
```

Restart and everything came up 800x600 and looks great!

~ 'Stump

---

### Post by Djsands on 2006-12-05
I don't know if this will help any one. but i found something on Dell's site about the xconfiguration. it's for the inspiron line in general is seems. I ended up installing PCLinuxOS and things appear to be working completely fine. But i found this and remeber how much time i took to look for stuff.

[Journal: 063397HF9V]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?docid=314105A03DE14E1F901CBFF56A04036D&c=us&l=en&s=gen")


Table of Contents
1. How to make Xwindows in RedHat Linux 6.1 run on my Dell™ notebook.

1. How to make Xwindows in RedHat Linux 6.1 run on my Dell™ notebook.

After properly configuring Xwindows, the program still may not start correctly. This may be due to incorrect video settings. A line of text can be inserted into the lilo.conf file in order to boot into a different video mode.

NOTE: This solution applies only to Dell notebooks that have an optimal resolution of 1024 x 768. Please check [http://support.dell.com](http://support.dell.com) to make sure that your optimal resolution is 1024 x 768.


To insert the line and change the video settings, complete the following steps:

   1. When the login prompt appears, log in as root and press <Enter>.
   2. When the password prompt appears, type in the root password and press <Enter>.

      NOTE: The default root password for Dell Americas computer systems is dell, and for Dell Europe systems the password is dellinux.
   3. Type in Xconfigurator and then press <Enter>.
   4. Press <Enter> again to go past the Welcome message.
      Xconfigurator will detect your video chipset. 
   5. Press <Enter> to continue.
      You will be prompted to select a monitor.
   6. Choose LCD Panel 1024x768 and the press <Enter> to continue.
   7. Press <Enter> again to choose Don’t Probe.
   8. Choose 2 mb and then press <Enter>.
   9. Press <Enter> again to choose No Clockchip Setting.
  10. Press <Tab> to switch to the 16 bit column. 
  11. Press the <Down arrow> twice and then press <Space> to select 1024x768.
  12. Now press <Tab> twice to select Ok, and then press <Enter>.
  13. Now press <Tab> to select the Skip option. Then press <Enter>.
  14. Type pico /etc/lilo.conf at the command prompt and press <Enter>

      NOTE: Pico is just one of many text editors available. Other text editors should work as well.
  15. Insert vga=791 as a new line of text at the beginning of the file.
  16. Save and exit the program.

      NOTE: If you use Pico, press <Ctrl><O>, and then <Ctrl><X>.
  17. At the command prompt, type lilo and press <Enter>.
  18. Restart the computer by pressing <Ctrl><Alt><Del>.
      You should now notice a graphic of a penguin in the upper left hand corner of your LCD.  If not, please retrace the steps, starting at step 1.
  19. Log in again as done in steps 2-3.
  20. At the command prompt, type startx and press <Enter>.

Xwindows should now start with the proper video settings.

---

