---
title: "About Adsl usb modems and Huawei brand."
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by Bulltitan on 2006-05-31
Ok i have tested these drivers and procedures with: Ubuntu 5.10, Kubuntu 5.10, 
Ubuntu 6.06, Xubuntu 6.06. The last one is the one i'm using right now and i can 
tell you i love it, it has some problems but is simple to use, fast and so far solid.
Now how i did it:
1- Be sure to have installed in your fresh ubuntu the "gcc" compiler all of it just in    case,  the "c++" compiler you'll be ok with the 4.0 but if in doubt mark them all,
 kernel headers (very important), the "libc6-dev" library. I know that maybe this is
 not required to compile the file but i also marked "alien" and "rpm" .

2- The drivers: For any ubuntu 5.10 use "eagle-usb-2.3.2", for any ubuntu 6.06 use
 "eagle-usb-2.3.3" wich you can get from the eagle site in french,... i can't 
 remember the url now. 
 Now you need the rp-pppoe-3.06 to have pppoe support specially in ubuntu 6.06.

3- It's time to compile, unpack the eagle usb package and the rp-pppoe package 
anywhere you want.
Firs you need to install the rp-pppoe package so get inside the src subdir of the
rp-pppoe unpacked folder and type in a console as root:

./configure
make
make install

If everything was ok you'll see something like "now type pppoe-setup to configure" 
do the setup and enter your connection info.

Now we need to install the eagle usb driver to do this go inside the eagle-usb  unpacked driver and in a console as root type:

./configure
make
make install

if everything was ok then you need to type "eagleconfig" to configure the eagle
driver. After finishing the eagle configuration the modules will be loaded and the
modem will try to syncronize, if you see the power and link light on the go ahead
and type in your console "startadsl"

Maybe you'll need to configure some files like "eagle-usb.conf" , "eagle-usb.conf.template" (the content of this two files must be the same), "resolv.conf" and "pppoe.conf" leave pppoe.conf alone if you configured it before 
with pppoe-setup.
For eagle-usb.conf go to:

cd /etc/eagle-usb/
gedit eagle-usb.conf (you must be root!)

Verify the VCI and VPI numbers in my case it is
VPI: 000000
VCI: 0000021

After making changes save the file.

Now open eagle-usb.conf.template

gedit eagle-usb.conf.template

Check it's content and make sure it matches the one in eagle-usb.conf, save the 
file.

Now you need to edit the resolv.conf file to enter the dns information.

cd /etc/ppp/
gedit resolv.conf (remember at all times to edit in root mode)

in my case i use the dns provided by my isp:

nameserver 200.45.0.115
nameserver 200.45.0.116

Now save the file and one final step ahead to make the dial process easyer,..
go back to the unpacked rp-pppoe folder and in a console as root run the go-gui 
script, this will open a little dialog that let's you enter your isp account information 
after saving it just press the start button and you'll be connected.
To call this little gui dialog type in console "tkpppoe"

I've also installed the ati fglrx driver in each distro with no problems at all just
follow the thread "HOWTO: Fixing the "Mesa Issue" and getting fgrlx for ATI Cards"
it works every time, thanks to escape and all the people adding info to that thread.

Sorry if i had any errors, feel free to correct the info in this thread and add 
more info to it, i hope this helps someone.

---

