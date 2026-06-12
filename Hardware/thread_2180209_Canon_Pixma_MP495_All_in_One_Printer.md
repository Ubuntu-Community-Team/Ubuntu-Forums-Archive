---
title: "Canon Pixma MP495 All in One Printer"
date: 2013-10-12
forum: Hardware
---

### Post by digitalmetis on 2013-10-12
Hi! :)

I've searched through many websites to find information on how to setup the Canon Pixma MP495 All in One Printer in Ubuntu 12.04. Most of the guides pertain to Ubuntu 10.10. However, new Ubuntu releases up to 12.04 may work as well. 

Please help in making this guide more thourough, and simple to follow.

Wireless Printing Setup for Canon Pixma MP495

Setting up your router:

You will need to find the default internal IP address of the router you are using by looking in it's manual.
If you don't have a manual for your router, open your web browser and navigate to [www.google.com](www.google.com)
Now enter your router's make and model and click search.

If you can't find your routers default internal IP address, you can try one of the three common internal IP addresses below by entering into 
your web browsers address bar and pressing enter. 

Common internal IP addresses for routers are;
192.168.1.1
192.168.0.1
192.168.2.1

If you have found the internal IP address of your router in it's manual, or online, enter the internal IP address into your web browsers address bar and press enter.

(There are several web browsers for Ubuntu, but they all have an address field. It's where you enter "www.google.com" without the quotations. Rather enter the IP address of your router)

Before you continue to change settings in your router I suggest you do the following;

1. Write down the SSID of your router.
2. Write down the encryption method you're using. The router is normally set to use either WEP or varients of WPA.
3. Write down the password you use to connect wirelessly to the router.

Now you are going to replace the Router's SSID to the default SSID that the printer is currently using.
(The SSID is case sensitive so you will need to enter the followng SSID in uppercase.)

Once you have found the SSID field in your routers settings, replace it by enter the following ;

BJNPSETUP

Now remove all security features your router is currently using.
(I suggest reading your manual to do this, as it will guide you through this process.)

Once you have completed removing the securty features, save and apply the changes made to your router.
(The router may ask to confirm the changes made and restart.)

Setting up your Printer's WIFI:

Reset all wireless settings in the printer by going to the "t" looking letter (the one after the G-shaped letter) and pressing Color and then start the scanner again.

Now press the maintenance button on the printer 13 times until you see what looks like a capital G without the middle line.

Then press the color start button.

(You should see the wifi light on the front of the printer turn on and be solid not be blinking)

Finding the Printer's IP address:

Open your web browser to download Angry IP Scanner packages for 32 or 64 bit.
(The following packages can be found at [http://angryip.org/w/Download](http://angryip.org/w/Download))

For 64 bit click here [http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.2/ipscan_3.2_amd64.deb](http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.2/ipscan_3.2_amd64.deb)
For 32 bit click here [http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.2/ipscan_3.2_i386.deb](http://sourceforge.net/projects/ipscan/files/ipscan3-binary/3.2/ipscan_3.2_i386.deb)

Save the compatible package to your downloads folder.

Go to your application menu and run the program called "Terminal".

Now copy and paste the following into the Terminal;

```
cd Downloads/
```

press enter

If you're using 64 bit package, copy and paste the following into the Terminal;

```
sudo dpkg -i ipscan_3.2_amd64.deb
```

press enter

Continue by entering your Ubuntu password.

press enter

then copy and paste the follwing into the Terminal'

```
sudo apt-get update
```

press enter

then copy and paste the following into the Terminal;

```
sudo apt-get -f install
```

press enter and you're done.

If you're using 32 bit package, copy and paste the following into the Terminal;

```
sudo dpkg -i ipscan_3.2_i386.deb
```

press enter

Continue by entering your Ubuntu password.

then copy and paste the follwing into the Terminal;

```
sudo apt-get update
```

press enter

then copy and paste the following into the Terminal;

```
sudo apt-get -f install
```

press enter and you're done.

Using Angry IP Scanner to find you printers local IP address

Search the applications menu and click Angry IP Scanner

In the IP Range field on the left replace the last three numbers to 1
In the IP Range field on the right replace the last three numbers to 254

Then click Start

When the search completes, scroll down and search for a hostname similiar to...

```
A001BF000000.local
```

To the left of that you will see the printers IP.

Copy and paste the printers IP into the web browsers address field and press enter

Click Other Settings in the left hand column, and set LPR Service Notification to ON

Change the printers SSID to the original one you used on the router.
(The SSID the tutorial request's you to write down)

Then change the encryption to what you use on the router
(WEP or WPA)

Save and apply settings.

Connect again to the Router

Now enter your routers IP address in your web browsers url field and press enter

Replace the SSID and activate all security features you originally wrote down for your router.
(These need to match the changes you made to the printer)

System Settings

Go to applications and click System-Settings

Click the Printer icon

Click the Add icon

Click the Network icon

Select your Printer and click forward
(The computer will now search for it's driver)

A second window will appear asking for the description of the printer

you can enter something similiar to

```
homeprinter
```

Enter this in the URI field

```
URI lpd://[replace with printer-ip]:515
```

Installing Canon Pixma MP495 All in One Printer Drivers

IMPORTANT: The Canon site for these drivers [http://support-au.canon.com.au/contents/AU/EN/0100301501.html](http://support-au.canon.com.au/contents/AU/EN/0100301501.html)
has this disclaimer "Canon Driver Downloads is for the support of Canon Products SOLD IN AUSTRALIA AND NEW ZEALAND ONLY."
So these drivers may not work in North America.


To download the drivers click this link [http://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwMjM2MTAy&cmp=ABS&lang=EN](http://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwMjM2MTAy&cmp=ABS&lang=EN)

Save the file to the Downloads folder

Right click the package cnijfilter-mp495series-3.40-1-deb.tar.gz and choose extract here.

Open the folder cnijfilter-mp495series-3.40-1-deb

If you are using a 64 bit Linux then click these two files to install.

cnijfilter-common_3.40-1_amd64.deb and cnijfilter-mp495series_3.40-1_amd64.deb

If you are using a 32 bit Linux then click these two files to install.

cnijfilter-common_3.40-1_i386.deb and cnijfilter-mp495series_3.40-1_i386.deb

---

### Post by scbingham on 2013-10-12
From memory, that all looks ok. Apart from a few grammatical errors ;)

The most confusing part is trying to understand the printer's instruction manual lol; particularly how many times you have to press the button to find the 'G' symbol. 

I also set my printer's ip address to one outside of the router's dhcp range.

I used a spare router to set mine up, as other people share the network (kindly provided by our landlord :p)

You might wish to add something about installing scangearmp for the scanning capabilities.
I downloaded & installed scangearmp-mp495series-1.60-1-deb.tar.gz
Then I created a desktop icon which calls /usr/bin/scangearmp

---

### Post by digitalmetis on 2013-10-12
> **scbingham said:**
> From memory, that all looks ok. Apart from a few grammatical errors ;)

The most confusing part is trying to understand the printer's instruction manual lol; particularly how many times you have to press the button to find the 'G' symbol. 

I also set my printer's ip address to one outside of the router's dhcp range.

I used a spare router to set mine up, as other people share the network (kindly provided by our landlord :p)

You might wish to add something about installing scangearmp for the scanning capabilities.
I downloaded & installed scangearmp-mp495series-1.60-1-deb.tar.gz
Then I created a desktop icon which calls /usr/bin/scangearmp

Grammer is very difficult for me due to my illness. Or it could be my education ;) Either way thanks for replying. If you can point out the errors I appreciate it.
I'm going to add scanning to the post after I finish correcting any possible errors.

---

### Post by scbingham on 2013-10-14
Just add the bit about scanning.

If there are any errors, I'm sure anyone who follows it will point them out & then you can amend it. Only way to test your notes would be to delete everything & do it all again. Mine works, so I'm not too keen to do that but I reckon it all looks fine.
However, if I get time I'll go through it on my other machine & let you know.
I have read that some use xsane for scanning. Not sure if that's something you'd want to look into, Scangear works perfectly for me.

---

### Post by starlyte2 on 2013-11-14
Thanks for this. I use Puppy Linux based on Lucid, so this really helps a lot, as Puppy Lucid is a sort of condensed form of Ubuntu Linux. Very practical, as it's portable, and under 1mb. It's been my main OS since 2002, as it's so versatile, and uses Ubuntu and Debian softs. I'll post back when I've set up my Canon, AND my wi-fi reseau (first ;) )

---

