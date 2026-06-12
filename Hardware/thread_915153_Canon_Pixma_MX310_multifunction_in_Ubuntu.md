---
title: "Canon Pixma MX310 multifunction in Ubuntu"
date: 2008-09-09
forum: Hardware
---

### Post by commbba on 2008-09-09
Hello there.I recently bought the Canon Pixma MX310 multifunction machine , although I found ,after googling ,that it is possible not to work in Linux based systems.
Although I've installed the gutenprint driver and the Pixma MP520 and MP610 drivers the machine don't work.
Someone made this machine to work with the gutneprint multidriver with the CUPS driver.I searced to do it so ,but I can't even understand how to download it , nor to install it.
Is there anyone volunteer to guide me step by step how to install all these drivers ,except the gutenprint ,and there is also an open source driver for the scanner.I need help in this section , too.
Sorry ,for my overall demands but my console level is tooooooo low and in my time with the Ubuntu OS I must say that it is rather difficult for a middle user to make his changes to the OS.

---

### Post by commbba on 2008-09-12
Hello again ,I'm back.Thank you for viewing my thread and not hard feeling because you didn't answered me . I know is very difficult to guide someone step by step and also every machine needs special treatment depending the hardware.
Now about my problem , I solved it and the solution was rather easy and in front of my eyes.
I entered System->Administration->Printing(saw it in another thread) and deleted all the entries depending the particular printer.Then pressed ''Add new printer->selected Canon MX310 series USB #1->select printer from database(Canon and then model Pixma MP150 which is the most familiar to my model,no MX310 option) and print a page from my computer.It worked.
Now I have to do something for the scanner.:guitar:

---

### Post by drpaul on 2008-09-12
For the scanner you should go to the SANE forum or list and see if anyone has had any experience with your hardware.

HTH

Paul

---

### Post by commbba on 2008-09-13
I've already searched the internet for sane and canon printers , but all the suggestions looks greek for me , despite that greek is my native language.
I found this site [http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html]("http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html") and tried out all the acts mentioned there , except 2 which the konsole couldn,t execute , but the conclusion is that the scanner still isn't recognised by the system.

---

### Post by commbba on 2008-09-13
I found also this site[http://mp610.blogspot.com/]("http://mp610.blogspot.com/") but I'm stuck in the ''./configure.....'' section.The konsole answers me command not found.

---

### Post by commbba on 2008-09-13
The good part is that SANE is an acronym , stands for Scanner Access Now Easy.If this is the easy way to make functionable a scanner that it is supporting by the developers , which is the difficult way.Two days know I'm searching the net for possible solutions , I've entered so many codes that I have never entered before , but the result is the same.No scanner for a machine that it is supporting by the developers of SANE and an unhappy headache.
I'm giving up for a couple days to think better and start over again.

---

### Post by commbba on 2008-09-22
Now I'm starting to figuring out what is going on.
My scanner is being supported by the unstable version of SANE.
----------------------------------------------------------
When I'm typing sane-find-scanner , the answer is :
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9, product=0x1728) at libusb:004:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
----------------------------------------------------------
When I'm asking for scanimage -L , it answer's :

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
----------------------------------------------------------
And for scanimage -V , the answer is :
scanimage (sane-backends) 1.0.19; backend version 1.0.19 , when I found in an earlier site that the version of scanimage was 1.1.0 !!!!!!!!!!!!!!!!!

---

### Post by FlippinReilly on 2008-12-29
Thank you so much for the info,:KS I was paralyzed until I found your post.  The scanning is really important for me, but I can't understand your instructions- how did you get it to work?

Any chance you could translate this for a novice?  A step-by-step would be great.

---

### Post by PyraGorgon on 2010-01-29
I am having a dreadful time trying to figure out how to get my Canon PIXMA MX310 "All in one" machine to work as well. The printer device list keeps coming back telling me it identified a "Canon PIXMA MX310 FAX" but not a printer...

...so I tried to configure the fax with the menus provided with the basic installation of Xubuntu "Karmic Koala" 9.10 (stable)---> it wont recognize the fax machine.

After doing some Internet searching on this topic, I discovered in some of the "Add/ Remove Applications" a few programs that *seemed* to address this. Since I am as green as a springbud to all this computer code programming and line commands, the explanation for how to create my own drivers and install these into my Xubuntu system was way over my head.

I guess what I am asking here is this--> HAS this Canon PIXMA MX310 PRINTER machine issue been sucessfully solved with a driver somewhere? If not, then what are my options? 

P.S. the README and HELP files associated with the Karmic Koala basic install are not very helpful with this problem. I am still running Windows XP side by side with Xubuntu on a partitioned harddisk. I was curious if maybe I could somehow import the program across the partition???

By the way, My laptop computer is a HP Pavilion dv5120us model AMD Turion 64 processor with ATI Radeon. IF any of that info is helpful to figuring this out.

Thank you for any input or guidance on this.

---

### Post by farish on 2010-01-30
I got mine to work with the 150 driver recommended above.

---

### Post by PyraGorgon on 2010-01-30
> **farish said:**
> I got mine to work with the 150 driver recommended above.

Thank you for that information! I did find since posting this query to the awesome community network of Ubuntu users that if I install the Canon PIXMA MP220 driver that I can get the printer to print images of outstanding quality plus it also allows me to tweak page setup settings. (I got a weird scriptie-looking thing that asked if I wanted to modify driver, and said yes to it. I got a message that said that "CUPS /+1" or something like that)
** {I cannot find how I did that again, so the <<  / +1 >> is not a exact thing that I will say absolutely. something about the driver being added to is all I can tell}**

However, with the above modified driver from the PIXMA MP220 I do not have any drivers to work any other functions of my "all-in-one" machine. The FAX, SCANNER, and COPIER elements still dont function, nor can I access any of the maintenance features of my PIXMA MX310. :frown:

---

### Post by Jason Argonaut on 2010-05-16
> **PyraGorgon said:**
> Thank you . . . . .  . . .maintenance features of my PIXMA MX310. :frown:


PyraGorgon is your machine x86 or amd46?

My Canon MX320 USB doesn't work on my amd64 Ubuntu Lucid Lynx.

[http://ubuntuforums.org/showthread.php?t=1313992](http://ubuntuforums.org/showthread.php?t=1313992) 

Thanks.

---

