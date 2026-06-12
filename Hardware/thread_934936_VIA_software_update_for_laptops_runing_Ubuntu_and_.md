---
title: "VIA software update for laptops runing Ubuntu and compiz.........."
date: 2008-10-01
forum: Hardware
---

### Post by jakewc2 on 2008-10-01
I am using a laptop with VIA software, and have been in contact with VIA, about an update to get compiz working with their products. 

I got a bit of a garbled e-mail back, I think because it was from Taiwan, but it pointed me to their site, and a linux page.

I was pointed to this page

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

and told to run this command "uname -r" to make sure the kernel version is 2.6.24-16 or 2.6.24-19. I was also told that I needed to be able to modify the xorg.conf for the LCD of your laptop. 

I was left no other instructions. I sent the e-mail off on the 18th of this month, and it was replied to yesterday. I sent them a message back asking for more info, but dont expect and answer back too soon.

Can somebody help me with installing the patch, as I have no clue about what they are talking about. I have only been using ubuntu for a couple of weeks, and this is just way beyond me. 

Thanks.

John.

---

### Post by pihhan on 2008-10-01
I found one archive with Ubuntu driver and i see there somehow good instructions to install it. There is installation script, that might work (or not, i cannot test that).

From what i see, you have to download beta driver. I tested first in list to see what is inside. You will need very basic unix skill to do this.

unpack it somewhere. From terminal, command:

tar xzf path-to-driver.tar.gz

cd path-to-extracted-dir/

sudo ./vinstall

it might damage your ubuntu, i dont know how much that does work. There are also instructions in file. There is viaxorg.conf file, that is file script will put to /etc/X11/xorg.conf. That is where your current Xorg configuration file is. It will backup it, you can restore original if that havent worked, but run vinstall script only once! you might backup it using

cp /etc/X11/xorg.conf ~/xorg.conf 

to your home yourself.

To edit /usr/sbin/compiz, you can use sudoedit command. To use nano, instead of default vim, use:

EDITOR=nano sudoedit /usr/sbin/compiz

locate line mentioned in README file and append at end "via".
If you are beginner with ubuntu, i suggest you live without compiz until someone makes package or take time and read several articles about sudo, basic linux commands and that. 

Driver installation in linux are not click and point, especially from external sources. So, become skilled enough to install them or live without them. Any other solution will make you problems sooner or later.

Some articles:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

