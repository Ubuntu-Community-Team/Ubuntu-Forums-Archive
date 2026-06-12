---
title: "Need help installing ati driver"
date: 2010-07-16
forum: Hardware
---

### Post by devin0 on 2010-07-16
I just did a fresh install of ubuntu and am trying to get my ati card driver installed. I am unsure of how to do this, can someone help? I don't even know what ati card I have installed, Im not too familiar with linux and don't know where to go to find out the ati card number, if you can tell me the command to run to find out I can post the result.

Thanks

---

### Post by staf0048 on 2010-07-16
***Just realized this is a Lubuntu question.  Not sure if the below still applies as I've never used it***

Open a terminal by going to Applications/Accessories/Terminal and type:

```
lspci
```

look for anything that says video card or graphics card.  It should look something like:  ATI Video Card [Radeon 9600] or something similar.  That will tell you exactly what card you have.

Couple of questions though.  Are you still running Hardy?  If so, try installing a program called "envy-ng" it will detect your card and install the correct driver for you.  

If you're on Lucid your only option may be the Open Source driver (like me), but you can try going to ATI's site and attempt to install their proprietary driver.  Simply download the driver for your card, extract the contents of the downloaded file, then go to a terminal and "CD" to the directory you extracted the files to and run

```
sudo sh ati
``` hit tab to finish off the rest of the file name properly and enter.  Hopefully that works.

***Oh and don't forget to remove whatever current driver you might be running.  Check out my sig and follow the instructions there for more help***

---

### Post by cavalier911 on 2010-07-16
Menu/Preferences/Hardware Drivers

---

### Post by devin0 on 2010-07-16
OK i ran lspci and it told me i have a "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]" I started downloading the linux driver from the ati site like you said, however i still dont understand how to remove my current video driver. I took a look at the link in your comment, but didnt find anything about removing a current driver. would you be able t tell me how to remove whatever current driver i am using?

---

### Post by staf0048 on 2010-07-16
check out this link.  

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20to%20Install%20the%20fglrx%20Driver%20for%20Ubuntu%208.04%20(Hardy)%20and%208.10%20(Intrepid)%20from%20the%20Ubuntu%20Repositories](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20to%20Install%20the%20fglrx%20Driver%20for%20Ubuntu%208.04%20(Hardy)%20and%208.10%20(Intrepid)%20from%20the%20Ubuntu%20Repositories)

It will probably do a much better job of explaining the steps you need to take for your system better than I can.

It's possible that you're just running the generic vesa driver, in which case you may need to remove anything.  Hope this helps!

---

### Post by devin0 on 2010-07-18
Ok I understand those instructions there are of great help, but when it comes time to choose which version f the .deb packages to build I don't see my version of ubuntu in the list (10.04). Will it cause some kind of problem if i choose another version of ubuntu instead of 10.04? I ran this command```
sudo sh ./ati-driver-installer-9-3-x86.x86_64.run --listpkg
``` to tell me what packages to make and the one from the tutorial didn't show up in the list. Which should i choose?
```

Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source
```

---

### Post by staf0048 on 2010-07-18
Looks like your in the same predicament as me.  ATI has stopped updating your driver for newer versions of Ubuntu.  They've moved on to supporting other cards.  So, you can either go with the open source driver or downgrade your OS to an earlier version of Ubuntu.

You could try choosing the "source" option in the list, but I've never tried that myself.

---

### Post by devin0 on 2010-07-18
Ill give the source option a go here and if I have no luck with that then ill downgrade to 9. I Just installed recently so I don't really have to worry about losing anything. Is there any large drawback to being version 9 of ubuntu instaed of 10.4?

---

### Post by staf0048 on 2010-07-19
Post back with your results of the "source" option.  I'd be interested to know if/how it works.

I don't think there are too many draw backs with downgrading to 9.10.  Less support time, 18 mos from releasee date vs. 3 years for 10.04.  Maybe some older packages in the software center, but they should still be good enough for what you need.

Let us know your results!

---

