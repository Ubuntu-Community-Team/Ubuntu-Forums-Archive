---
title: "How to install driver for Realtek ALC268 (HDA) for Acer Aspire 4710 laptop"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by vigyani on 2007-09-23
Hi
I have an Acer Aspire 4710 laptop; headphones were not working on Ubuntu 7.04 feisty. I installed the driver for Realtek ALC268 HDA and now head phones work fine.


Make sure that your system is updated (including the kernel and libncurses5-dev) and ready to compile the drivers: update and then use the following command to make sure that all the libraries and packages are installed for compiling the sound driver:

*sudo apt-get install build-essential linux-headers-generic libncurses5-dev*

Download the driver from the 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs")
go to the Linux/Unix section and then clink on one of the links and download and save this file on your harddisk:

Open home folder: click on Places--> Home folder

Create a folder Software (you can put all your downloaded packages in this folder for future reference)

Move the downloaded file (as on Sep 23 2007 realtek-linux-audiopack-4.06c.tar.bz2) to the Software folder.

Start a terminal by clicking on the terminal icon on the bar on the top (or click on Applications--> Accessories --> terminal

on the terminal window type this command to change to Software folder:

*cd Software*

Then type the following command to unpack the downloaded file (as on Sep 23 2007 it is 4.06c; actual name would depend on the latest driver available; download the latest depending upon the Kernel Ver.):

t*ar -jxvf realtek-linux-audiopack-4.06c.tar.bz2 *

this unpacks the file and create a directory by name realtek-linux-audiopack-4.06c

then change to the directory:

*cd realtek-linux-audiopack-4.06c*

type the following command to compile and install the driver:

*sudo ./install*

It would show lots on info on the screen while driver is complied and installed;
After the driver is installed a configuration screen pops up

Configure the system according to your preference:

It would play a sound; if you hear the sound; it working; Enjoy.

You may have to configure front speaker and headphone volumes.


regards
Vig):P

---

### Post by vigyani on 2007-09-29
After Kernel update sound stopped working on the laptop; I just executed the command to install the driver once again. I think it would put the driver in the directory corresponding to the new kernel ver.
It works fine again.:)

---

### Post by rowanq on 2007-10-09
I have a question regarding this approach; if one uses the realtek hda driver does the jack sensing technology then work. That's the one thing I can't seem to find a fix for and it seems to be a drive issue.

rowan

---

### Post by vigyani on 2007-10-10
jack sensing does not work; but you can manually control the volume for inbuilt speaker or the headphones; i.e. you can make speaker volume off and headphone volume at the desired level. This is the best I could do.

Vig

---

### Post by rowanq on 2007-10-10
Thanks, that's exactly what I needed to know.

 Cheers!
rowan

---

### Post by axold on 2007-10-25
HI! I'm in trouble because i did all you said and... i don't have any sound, no speaker, no headphones... nothing and alsa didn't detect anything... if i execute alsamixer for example, tells me that there isn't nothing device.
I compiled the driver well, but nothing... what can i do?
thx a lot!

---

### Post by vigyani on 2007-12-26
Hi

Above solution is for the Ubuntu 7.04; apparently it did not work on Ubuntu 7.10. I did the following to make it work.

1. installed linux-backports-modules-generic

    sudo apt-get install linux-backports-modules-generic

2. added the following options line to /etc/modprobe.d/alsa-base:
    options snd-hda-intel model=acer

Now headphone plug mutes the speakers.

regards
Vig :guitar:

---

### Post by E_K on 2008-02-14
Hi, using 7.04 without and updates installed, on a acer extensa 5210, followed everything step for step, fingers crossed that i didnt loose all sound. 

I still have sound, but no headphones :(

any ideas?

---

### Post by sanjeevan on 2008-04-17
i get this error:
./install: 101: alsaconf: not found

---

### Post by ghonz on 2008-04-17
as do i
> **sanjeevan said:**
> i get this error:
./install: 101: alsaconf: not found

---

### Post by jagdishrao on 2008-04-28
hello all

i just tried the latest version and same error
any help appreciated

Linux driver (2.4 or 2.6) 5.01	2008/2/20	4624k

---

### Post by casual0402 on 2008-05-28
hi,first thanks for your article;
but at the end of the course , I got an error:

            ./install: 101: alsaconf: not found

yes,as above;            if you have any idea ,would you please contact me at 
                       [email]lijunpeng_20@163.com[/email] ?
thanks.

---

### Post by morgaen on 2008-06-07
Hi,
Does anybody have a fix to the error reported?

./install: 101: alsaconf: not found error

Thanks

Morgaen

---

### Post by vigyani on 2008-06-17
Hi

Did you try [http://ubuntuforums.org/showpost.php?p=4016762&postcount=7]("http://ubuntuforums.org/showpost.php?p=4016762&postcount=7") ?

After doing those two steps; reinstall the sound driver.

regards
vig

> **casual0402 said:**
> hi,first thanks for your article;
but at the end of the course , I got an error:

            ./install: 101: alsaconf: not found

yes,as above;            if you have any idea ,would you please contact me at 
                       [email]lijunpeng_20@163.com[/email] ?
thanks.

---

