---
title: "Mounting microsd card with 16.04 thru gopro session"
date: 2016-07-07
forum: Hardware
---

### Post by davehenson on 2016-07-07
First I'd like to say thanks to the greatest forum around! You guys have been so helpful in the past. 

I have a gopro 4 session with a 32gb microsd card in it. I know there are vids already on the card. when I plug in the camera via usb, I can see the gopro mounted in the (gui) file manager. I can go into it and see 2 folders "DCM_00000001_00000001" and "DCM_00000001".  Also there is a url shortcut to "get started with gopro.url". the top of the window of the file manager says "contains digital photos". Going into either of those folders I see no files.  I absolutely know there are 7 video files on the camera. 

this seems odd as it appears that the OS is reading the card as I can see the folders and the url. Has anyone else seen this before? Tips appreciated!

OS Ubuntu 16.04, microsd 32gb from micro center, firmware on the camera is current.  I also read around on the forum and found a thread that said to make sure exfat is installed. 
```
[COLOR=#000000][FONT=&amp]sudo apt-get install exfat-utils exfat-fuse
[/FONT][/COLOR]reboot
```

I can plug into my windows computer and all works fine but I want to kick windows to the curb!

thanks!!!

---

### Post by davehenson on 2016-07-11
just a polite bump?  anyone here running gopro cameras with Ubuntu at all?

---

### Post by nicolas.bernaerts on 2016-08-20
I also faced the same problem under UbuntuGnome Xenial and a GoPro Session Hero 4.

Problem comes from a bug in libgphoto2. This library needs to be updated to version 2.5.10 to solve the problem and to get back a full access to your GoPro.

I've explained the needed steps in this article [http://bernaerts.dyndns.org/linux/74-ubuntu/347-ubuntu-xenial-gopro-usb-access-bug](http://bernaerts.dyndns.org/linux/74-ubuntu/347-ubuntu-xenial-gopro-usb-access-bug)

Cheers.

---

### Post by davehenson on 2016-10-28
> **nicolas.bernaerts said:**
> I also faced the same problem under UbuntuGnome Xenial and a GoPro Session Hero 4.

Problem comes from a bug in libgphoto2. This library needs to be updated to version 2.5.10 to solve the problem and to get back a full access to your GoPro.

I've explained the needed steps in this article [http://bernaerts.dyndns.org/linux/74-ubuntu/347-ubuntu-xenial-gopro-usb-access-bug](http://bernaerts.dyndns.org/linux/74-ubuntu/347-ubuntu-xenial-gopro-usb-access-bug)

Cheers.


OMG THANK YOU SO MUCH!!!!  I became so frustrated with Ubuntu's lack of gopro support that I changed over to Fedora for a while. Now that I see this patch, I'm back to Ubuntu!

---

### Post by Bucky Ball on 2016-10-28
You have no SD card reader? I simply whip the card out and put it in the computer. Done. I actually found that was the simplest and definitely the quickest for dumping large amounts of video data. No need for patches and other things. For the larger cards you do need exfat-utils and exfat-fuse installed. They are in the repos.

Transferring large amounts of video data directly from the camera is a yawn. Go make a cuppa. Straight off the card and takes seconds.

---

### Post by davehenson on 2016-11-08
> **Bucky Ball said:**
> You have no SD card reader? I simply whip the card out and put it in the computer. Done. I actually found that was the simplest and definitely the quickest for dumping large amounts of video data. No need for patches and other things. For the larger cards you do need exfat-utils and exfat-fuse installed. They are in the repos.

Transferring large amounts of video data directly from the camera is a yawn. Go make a cuppa. Straight off the card and takes seconds.

I need to get a microsd card reader and give that a try. I'm not sure why "where" its reading the data from would matter though.  Or would it? (I don't know, hence me asking.) Is there a difference in how the OS looks at the target? (SD card vs USB connection with card in the cameria)

---

### Post by Bucky Ball on 2016-11-08
I suppose with the camera the data needs to be processed from the card through the camera to the USB output on the camera and then through the USB cable and into the computer. With the SD directly in the computer it 'cuts out the middle man'; the camera. :-k

USB3 external card reader, if they make them and if you have a USB3 capable computer. Don't know whether you're using a laptop or desktop, but if laptop, thought that would have a reader in there. Sometimes they're hard to see.

---

### Post by yomgui2 on 2017-09-22
> **davehenson said:**
> ....
```
[COLOR=#000000][FONT=&amp]sudo apt-get install exfat-utils exfat-fuse
[/FONT][/COLOR]reboot
```

Thanks a lot really, it worked like a charm!!

I just eject, install exfat-utils and exfat-fuse, replug and I could access to my SDcard.

You are my hero!

---

