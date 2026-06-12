---
title: "WGET Problems"
date: 2009-12-17
forum: Hardware
---

### Post by DeltaFee on 2009-12-17
Okay I have no internet connection due to the fact I have to install bcmfwcutter. I have the file bcmfwcutter.deb and I have the wget that .deb wants. I have download and transferred both files to the laptop. What I need help with is installing the Bcmfwcutter.deb so that when it starts the wget to get the > wl_apsta-3.1.30.20.0.o file it gets it from the laptop so that it finishes the installation. :-# I am sorry if I sound bossy but I have been dealing with this for a month with no end and I've been getting weird responses. thx :-({|=

---

### Post by Tek-E on 2009-12-17
Wait so you need help installing the .deb file??
and then have wget grab wl_apsta-3.1.30.20.0.o?  Is that a file??

Sorry Im just trying to clear things up a little bit.  Im slightly confused by the way you described your objective.

---

### Post by DeltaFee on 2009-12-17
Yes I am trying to install the .deb and than have wget get the file that is on the computer instead of trying to get it off the internet.

---

### Post by Tek-E on 2009-12-17
To install the .deb file :
```

dpkg -i bcmfwcutter.deb

```

As for using wget to grab a file thats is already on your machine....  I am still looking into.  Why exactley do you need wget to grab a file you already have?

---

### Post by DeltaFee on 2009-12-17
When I try to install the .deb it does the wget and tries to download wl_apsta-3.1.30.20.0.o and since I don't have the internet connection it can't download wl_apsta-3.1.30.20.0.o which is why I had to download it from another computer and transfered it to the computer.

---

### Post by Tek-E on 2009-12-18
> **DeltaFee said:**
> When I try to install the .deb it does the wget and tries to download wl_apsta-3.1.30.20.0.o and since I don't have the internet connection it can't download wl_apsta-3.1.30.20.0.o which is why I had to download it from another computer and transfered it to the computer.

Oh okay. I see.  So the installation process of the .deb file automatically uses wget to grab the file??

hmmmmm.

So if I understand correctly.  Your problem then would be that wget is trying to access a web page storing the file that you obviously don't have access to.  

Here is what I would try (I am sure there is a much easier way to do this but this is my stab at it.)

- Get back to another computer and download the monkeyHTTP Daemon.  It lets you host web pages on your computer.  (really neat actually)

- Install and configure monkeyHTTP on your computer.  Set the default port at 80 which is the basic port for HTTP connections (Documentation on how to do that is included with the program)

- Then add the file wl_apsta-3.1.30.20.0.o on that web page. Same name and same path.

- Since wget will still try to grab the file with
```

wget http://www.somesite.com/path/to/file

```
add the name of the website to your hosts file which is in /etc/

So basically what you are doing is setting up a mock webpage to trick wget into grabbing the file off your computer rather than grabbing it off the internet.


I hope that made sense.  let me know if you have questions or need me to make things more clear.

That is probably not the simplest solution.  But it is what I would try.

- Since your

---

### Post by DeltaFee on 2009-12-18
I install monkey Http, but now I am kind of confused on how to use it. I believe I set the port to 80, but I don't know what the url is for the site, and I am not sure where to put the file.

---

### Post by coffeecat on 2009-12-18
I'm sure you've thought of this, but as no one has mentioned it, I will.

Can you make a temporary wired connection with an ethernet cable, simply to let the deb file do its wget thing? If the network you use can only be accessed wirelessly, is there any friend, relative or acquaintance who could let you use their internet connection?

---

### Post by KeLa on 2009-12-18
You can also install that monkeyHTTP on the computer you're trying to install that .dep and add 127.0.0.1 to have same name as the site that wget is trying to access.

---

### Post by DeltaFee on 2009-12-18
Unfortunately I can't the laptop has no network interface, except for PCMI card which is the wireless card that I am trying to get working. I've done it with older versions of xubuntu, where the .deb would ask if I had the file on the computer. However, I think I connect it through the cable modem with a USB cable Which I think I am going to have to do.

---

### Post by KeLa on 2009-12-18
Actually 127.0.0.1 is the localhost that is a "virtual" network interface or in other word a build in eth interface or loop back interface. You can use it even if you have no actual network card available.

---

### Post by IcarusR on 2009-12-18
Could you use another box to access internet, search for & download missing file? 
Then transfer file to other box with usb stick.

---

### Post by KeLa on 2009-12-18
> **IcarusR said:**
> Could you use another box to access internet, search for & download missing file? 
Then transfer file to other box with usb stick.

OP has explained already that program starts wget to download file from net.

---

### Post by coffeecat on 2009-12-18
I think I have a solution. You have both the bcm43xx....deb file and the wl_apsta-3.130.20.0.o file. Correct?

Put the .deb file somewhere convenient, right-click on it and choose 'Extract here'. You'll get a folder extracted containing the contents - control.tar.gz and data.tar.gz. Do an 'extract here' on data.tar.gz and you'll get a /usr folder containing /bin and /share folders. In the /share folder is yet another subfolder called /bcm43xx-fwcutter, and in that folder is the executable script install_bcm43xx_firmware.sh. The script in the version I downloaded consists of this:

```
#!/bin/sh

set -e

dname=wl_apsta.o
if [ -e /usr/bin/wget ]; then DL="wget -O $dname"; fi
if [ -e /usr/bin/curl ]; then DL="curl -o $dname"; fi

cd /tmp
$DL http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
bcm43xx-fwcutter $dname
mkdir -p /lib/firmware
for i in *.fw; do
        mv $i /lib/firmware/$i;
done
rm wl_apsta*.o
```But check yours. There were a few versions of the bcm cutter package to choose from. In the /bin folder is the executable bcm43xx-fwcutter. So, as far as I can see, all you have to do is put the bcm43xx-fwcutter executable and wl_apsta-3.130.20.0.o file in the same place, and do each command in the script from the 'bcm43xx-fwcutter $dname' line, adapting that to:

```
sudo ./bcm43xx-fwcutter wl_apsta-3.130.20.0.o
```The for - done loop you could probably do as a 'sudo mv *.fw /lib/firmware/'.

As far as I can make out bcm43xx-fwcutter must extract a number of *.fw firmware files from wl_apsta-3.130.20.0.o, which you need to move to lib/firmware. And that's it really.

---

### Post by DeltaFee on 2009-12-18
I did it and it extracted it, but I noticed its contained in a file which I can't seem to open even with sudo. so I moved the whole file in

---

