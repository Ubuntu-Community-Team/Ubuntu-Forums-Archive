---
title: "ubuntu 12.04 webcam issue"
date: 2012-07-17
forum: Hardware
---

### Post by xenosaga456 on 2012-07-17
so im running the newist firefox on ubuntu 12.04 LTS 64 bit and when im on sites like meatme.com or facebook i cant do video chats it wont pick up my web cam at all and i have restricted extras installed but flash dosenot give me the option to allow my cammera or not

---

### Post by irv on 2012-07-17
I tried to setup video calling in facebook and it wants to download and install a windows exe file which will not work in Ubuntu. so I don't think you can do this. I know Google + works for hanging out with friends and family. I've used this in Ubuntu.
Does your video Cam with with Cheese?

---

### Post by xenosaga456 on 2012-07-21
yes it works with cheese it just wont work on site i use it evin works with vlc and it wont work with any chat site on firefox ill try a diffrent web browser like chrom and let u know but i really whant it to work on firefox i know on an older version of ubuntu like 8.04 hardy heron i could synaptic package somthing called v-loopback and that did the trick but its no longer in synaptic now??

---

### Post by irv on 2012-07-21
I'm using Chrome Browser. Google+ hangout works with my cam. It needs a plugin, but it will install the first time you try to use it.
Maybe after the plugin is install your other sites will work?

---

### Post by kyme on 2012-10-19
You have alter the path from v4l1compat.so in 12.04 . 

New Path:
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
Old Path

Old Path: 
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

But before that, make sure you have installed the  libv4l-0
that install Ubuntu restricted extras.

Open the terminal then type this
sudo gedit /usr/share/applications/skype.desktop

Then you see this line 4 "exec=skype" (with out the quotes)
Change that line to this Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv41/v11compat.so skype'

save and exit then open your skype and test it. ;) 
In 12.04. You don't need to worry about cause most functionalities that
works in windows will now works in Ubuntu 12.04. ;)  
It's now more like less worries than Vista ;)

---

