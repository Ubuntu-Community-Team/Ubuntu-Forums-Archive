---
title: "Can't get scanner to work"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by David Haas on 2005-03-16
Xsane doesn't recognize that I have a scanner and the shell doesn't list it,  although Device Manager does.

According to the Sane Website, the Benq (formerly Acer) 640 BU scanner works with Linux. Its backend is snapscan, which in Warty is at /etc/sane.d. I've edited the snapscan.conf file to give the path to the needed firmware file, which I installed from the company's CD. The listed firmware file at the Sane site is u126v043.bin, but my CD had the file u126v039.bin. My understanding is that the last 3 integers are unimportant. I gave the path as: firmware /usr/local/bin/u126v039.bin, and have the firmware file at usr/local/bin.

Because no scanner was listed in /dev or in /dev/usb, I entered the text for it at /dev/usb (scanner0) and edited the snapscan.conf file to read /dev/usb/scanner0 bus=usb. However, at every boot up the listed scanner in /dev/usb is gone. 

What do I need to do to enable the scanner to work?

---

### Post by lordofkhemenu on 2005-03-16
My guess would be that you **have** to have **that** specific version of the firmware for the scanner (probably available [here]("http://www.benq.co.uk/serviceandsupport/downloads/downloads.cfm?product=89")) to work (*otherwise the SANE site would've mentioned other fw versions...*)

---

### Post by az on 2005-03-16
[QUOTE=David Haas]Xsane doesn't recognize that I have a scanner and the shell doesn't list it,  although Device Manager does.

According to the Sane Website, the Benq (formerly Acer) 640 BU scanner works with Linux. Its backend is snapscan, which in Warty is at /etc/sane.d. I've edited the snapscan.conf file to give the path to the needed firmware file, which I installed from the company's CD. The listed firmware file at the Sane site is u126v043.bin, but my CD had the file u126v039.bin. My understanding is that the last 3 integers are unimportant. I gave the path as: firmware /usr/local/bin/u126v039.bin, and have the firmware file at usr/local/bin.

Because no scanner was listed in /dev or in /dev/usb, I entered the text for it at /dev/usb (scanner0) and edited the snapscan.conf file to read /dev/usb/scanner0 bus=usb. However, at every boot up the listed scanner in /dev/usb is gone. 

What do I need to do to enable the scanner to work?[/QUOTE]

I installed this scanner for my father-n-law two years ago.  I though that the firmware went in /etc/sane or something.  Not /usr/local/.....

---

### Post by kleeman on 2005-03-16
Does sane see it when run with sudo? If so it could be a permissions issue. I did this ugly hack to solve my probs some time back:

chmod a+rw /proc/bus/usb/*/*

Then wacked it in /etc/init.d/local with a #! /bin/sh as first line.

Just a thought.....

---

### Post by c_dog on 2005-03-17
Try the firmware for the other Acer scanners like the 640BT u190v44.bin, u64v120.bin, or u96v121.bin. The Sane list said that my 620UT was supposed to work with the u64v120.bin, but it would not work. I tried the u96v121.bin that was listed for list for the 620U and it works beautifully (even better than it ever did in winbloze).  The 620s and the 640s are pretty much the same electronically. I just had to put the firmware location line in snapscan.conf. Didn't need to uncomment and edit the USB line.
 c_dog

---

### Post by David Haas on 2005-03-17
I appreciate receiving the suggestions about why I wasn't able to get my scanner (Benq 640BU)  recognized or operative. Before I got around to trying them, I got the scanner working perfectly, but I don't understand why this happened. Here's what I did: I ran into the /.dev directory by chance. I didn't know such existed. Here I saw that in the /.dev/usb directory, scanners 1 through 15 were listed, but no scanner0.  So, I added "scanner0" here with a mknod command (mknod /dev/usb/scanner0 c 180 48). Then I did the same in the /dev/usb directory, for no scanner was listed here, and when I had listed it with mknod before, it kept disappearing. I also found that with this, the Benq 640BU scanner listed in snapscan does not even need to have the comment mark edited out (deleted). What is the function of this hidden /.dev directory?

---

### Post by kleeman on 2005-03-17
Wow dude that is far out! I don't have such a directory here at all I just checked. Must be hardware specific or something ya got me.... :grin:

---

### Post by matchstich on 2006-12-15
i am trying to get my 620u to work. how do i get to snapscan.conf
i am really confused by all this.
complete newbie here
thanks

---

### Post by kleeman on 2006-12-15
sudo gedit /etc/sane.d/snapscan.conf

The fifth line of this file tells sane (the scanning software) where to find the scanner's firmware. Change the path (currently /usr/share/sane/snapscan/your-firmwarefile.bin ) to point to where the firmware is.

---

### Post by matchstich on 2006-12-15
thanks, i have the firmware in a folder on my desktop, how do i get it to whereever it needs to be
thanks
i have searched all over , is there somewhere i can read up on how to do stuff like this?

---

### Post by kleeman on 2006-12-15
Sounds like you need a basic primer on linux/unix:
Files are stored in directories. Your firmware will be in

/home/USERNAME/Desktop  (USERNAME is your login)

from what you have said. You want to move this somewhere more convenient for all users.
Open the gnome terminal and at the prompt type in

pwd

This should return /home/USERNAME
Now lets change to the Desktop directory

cd Desktop

let's now look whats in there:

ls -al 

You should see your firmware listed. Next let's move it somewhere more convenient

sudo cp  FIRMWARE  /usr/share/sane/snapscan (Replace FIRMWARE with the actual filename)

If you get an error saying this directory does not exist then create it with

sudo mkdir  /usr/share/sane/snapscan

and repeat the above step

Now lets tell sane where we have put it

sudo gedit /etc/sane.d/snapscan.conf

Got to the fifth line and change  'your-firmwarefile.bin' to the actual name of your firmware file
Save the file in gedit and then try scanning again

---

### Post by matchstich on 2006-12-15
-desktop:~/Desktop$ sudo cp U96v057.bin/usr/share/sane/snapscan

cp: missing destination file operand after `U96v057.bin/usr/share/sane/snapscan'Try `cp --help' for more information

thanks i got this.

---

### Post by kleeman on 2006-12-15
> **matchstich said:**
> -desktop:~/Desktop$ sudo cp U96v057.bin/usr/share/sane/snapscan

cp: missing destination file operand after `U96v057.bin/usr/share/sane/snapscan'Try `cp --help' for more information
U96v057.bin
thanks i got this.

There must be a space between U96v057.bin and /usr/share/sane/snapscan

---

### Post by gjtoth on 2006-12-15
> **kleeman said:**
> Does sane see it when run with sudo? If so it could be a permissions issue. I did this ugly hack to solve my probs some time back:

chmod a+rw /proc/bus/usb/*/*

Then wacked it in /etc/init.d/local with a #! /bin/sh as first line.

Just a thought.....

I was having a heckuva time with my Epson and this first line seems to have done the trick.... kind of.  Can you elaborate on the "
Then wacked it in /etc/init.d/local with a #! /bin/sh as first line."  portion of your instructions.  What's it do?  What do you mean "wacked it in"?

---

### Post by kleeman on 2006-12-15
I meant that you create a new file (say newsane) with the two lines

#! /bin/sh
chmod a+rw /proc/bus/usb/*/*

and then do

sudo cp newsane /etc/init.d/local

---

### Post by matchstich on 2006-12-15
/Desktop$ sudo cp acer/usr/share/sane/snapscan
then i got

cp: missing destination file operand after `acer/usr/share/sane/snapscan'
Try `cp --help' for more information.
 i put the bin back in the folder . there is no space, thanks
this scanner is drving me nuts.

---

### Post by kleeman on 2006-12-16
You need to read my posts carefully and probably buy a book on linux.

instead of 

sudo cp acer/usr/share/sane/snapscan

use

sudo cp acer /usr/share/sane/snapscan

See the difference? There is a space between acer and /usr/share/sane/snapscan the second time.

I assume that acer is the firmware file name?
If not replace acer with the correct name for the firmware file in what I said above.

---

### Post by matchstich on 2006-12-16
cp: cannot stat `acer': No such file or directory
-desktop:~$ pwd
/home/username
-desktop:~$ sudo cp acer /usr/share/sane/snapscan
cp: cannot stat `acer': No such file or directory
-desktop:~$ sudo cp u96v057.bin /usr/share/sane/snapscan
cp: cannot stat `u96v057.bin': No such file or directory
-desktop:~$ sudo cp U96v057.bin /usr/share/sane/snapscan
cp: cannot stat `U96v057.bin': No such file or directory
-desktop:~$

my apologies, i did not read your post correctly, but this time i did put the space in. 
also, to get that bim i did a drop and drag from the install disk, that was the correct way to do that, wasn't it.
appreciate you helping me. ist i did it with the bin in the folder , then i dragged the bin out of the folder and did it again. same result

---

### Post by matchstich on 2006-12-16
# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/your-u96v0567.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes 

dang it, did something right. cept my firmware is listed in here, say to change 5th line, that i dont know about, thanks
ok, i went back and re read  your instructions a few times, i put u96v057.bin in that blank line above "# nochanges", right? my scanner is a usb. my scanner is listed in the list under no changes.

---

### Post by gjtoth on 2006-12-16
> **gjtoth said:**
> I was having a heckuva time with my Epson and this first line seems to have done the trick.... kind of.  Can you elaborate on the "
Then wacked it in /etc/init.d/local with a #! /bin/sh as first line."  portion of your instructions.  What's it do?  What do you mean "wacked it in"?

Thanks very much.  Works like a charm.  :KS

---

### Post by matchstich on 2006-12-16
> **matchstich said:**
> # Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/your-u96v0567.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes 

dang it, did something right. cept my firmware is listed in here, say to change 5th line, that i dont know about, thanks
ok, i went back and re read  your instructions a few times, i put u96v057.bin in that blank line above "# nochanges", right? my scanner is a usb. my scanner is listed in the list under no changes.

i went to another thread and tried to do something in there.  cept now when i open snapscan.conf , it is blank
not sure what i did to it. thanks

---

### Post by matchstich on 2006-12-16
> **matchstich said:**
> i went to another thread and tried to do something in there.  cept now when i open snapscan.conf , it is blank
not sure what i did to it. thanks

ok, didnt know what to about the blank entry there, so i reinstalled ubuntu. so, now i just need to find out what to put on that 5th line, 
thanks

dang it, i messed upagain. i put acer in the command instead of the bin number, and now i can't put the bin, say directory already exist's. 
is there a way to overwrite that? 
thanks

---

### Post by matchstich on 2007-01-07
well, i went back and tried again. 
[http://www.ubuntuforums.org/showthread.php?t=317685&highlight=acer+scanners](http://www.ubuntuforums.org/showthread.php?t=317685&highlight=acer+scanners)

i posted the results there. can anyone explain to me what i did wrong? 
thanks

---

### Post by dbmk on 2007-01-22
I have the same scanner as matchstich
Acer 620U ( Vendor=04a5 ProdID=2060 )

And I have got it to work with ubuntu 6.06LTS
I have posted the method used to
[http://www.ubuntuforums.org/showthread.php?p=2047783](http://www.ubuntuforums.org/showthread.php?p=2047783)

But basically in ubuntu 6.06LTS

1- using info in table from [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)
- (firmware file u96v121.bin is needed)
2- get firmware file. u96v121.bin
- (extracted from driver downloaded from benq site)
[http://www.benq.co.uk/support/downloads/downloads.cfm?product=160&page=downloads&dtype=D](http://www.benq.co.uk/support/downloads/downloads.cfm?product=160&page=downloads&dtype=D)
3- install firmware file in ubuntu standard place
- /usr/share/sane/snapscan/u96v121.bin
4 - edit just one line in snapscan config file to u96v121.bin firmware
- /etc/sane.d/snapscan.conf

---

