---
title: "Fujitsu Lifebook A530 / AH530 and Ubuntu"
date: 2010-07-08
forum: Hardware
---

### Post by palmira on 2010-07-08
Hi,

while considering to purchase a Fujitsu Lifebook A530, my web search didn't reveal any information whether Ubuntu would or wouldn't run comfortably on that notebook. I hope we can do better and collect the experience Ubuntu users have had with the A530 so far.

For me, Linux compatibility is a must; the pre-installed Windows wouldn't even experience its first boot. At first sight, the hardware looks quite promising for Linux (that's essentially the reason why I'm interested in it): Intel Core iX processors, Intel HD graphics, Intel 802.11b/g/n WLAN -- I don't know the details about sound and webcam, but these features are, at least for me, not vital.

Are any happy/unhappy Fujitsu Lifebook A530 (or AH530) users around who can tell what works out of the box in Ubuntu and what does not?

Cheers,
palmira

---

### Post by eylonk on 2010-09-02
I have just installed ubuntu 10.04.1 on AH530.
So far it seems to work fine, WiFi is ok.
Didn't test the camera and the bluetooth yet.

---

### Post by cyberrobot on 2010-10-29
Hi,
I've just purchased a fujitsu AH530 series laptop and I was wondering if there is any proper driver for the brightness adjustment?

---

### Post by gomatteo on 2010-10-30
I'm considering to purchase an a530 too. Does someone know if the webcam work? And suspending/hibernating?

---

### Post by cyberrobot on 2010-10-30
> **gomatteo said:**
> I'm considering to purchase an a530 too. Does someone know if the webcam work? And suspending/hibernating?

I've installed ubuntu 10.04 with wubi-way at AH530GFX E-5, everything works fine (cam-suspending). Actually the cam works pretty good (my opinion). The only "bug" I found is with screen brightness, you can't adjust it,either fully bright or fully dark.

---

### Post by siju on 2010-10-31
> **eylonk said:**
> I have just installed ubuntu 10.04.1 on AH530.
So far it seems to work fine, WiFi is ok.
Didn't test the camera and the bluetooth yet.

What about sound quality ?

---

### Post by SyRenity on 2010-11-05
> **cyberrobot said:**
> I've installed ubuntu 10.04 with wubi-way at AH530GFX E-5, everything works fine (cam-suspending). Actually the cam works pretty good (my opinion). The only "bug" I found is with screen brightness, you can't adjust it,either fully bright or fully dark.

I installed 10.10 64-bit on AH530, all works great, including brightness adjustment (there are 5 levels).

The only issue is the power modes, the Eco doesn't seem to work.

Any power saving modes in Ubuntu?

---

### Post by SyRenity on 2010-11-05
> **siju said:**
> What about sound quality ?

Acceptable for VOIP, for music and movies consider using external speakers or earphones to go (these are not Lantec speakers inside after all).

---

### Post by diego.fiozzi on 2011-01-22
could anyone post alsa-base.conf?

it is in /etc/modprobe.d

i've a problem with audio...

---

### Post by jardo on 2011-03-25
i have been trying for 3 days in installing ubuntu 10.4, 10.10 and the same for kubuntu....without any success...
the installation take a lot of time and when it's finished and restarting computer it asks me in the console to log in...by the way i log in and write startx, but i get always dark display and i need to shut down.
it's an A530
with fedora everything works fine...any suggestion?
greetings

---

### Post by seb qwertzuiop on 2011-03-29
hi jardo,

my brother had a similar problem on his new A530 (installation from usb worked fine, after restart only the console, when he tried to start the "Xserver" the screen went black and nothing else happened).
He told me that he has found a website that explained how to fix the problem and now everything seems to work well. I asked him to send me the link to this page and i will post it as soon as I get his reply...  
perhaps it will work on your computer too...    :)

---

### Post by seb qwertzuiop on 2011-03-31
he could solve the problem using the instructions in in the first customer review here:
[http://www.google.de/products/catalog?q=fujitsu+lifebook+a530+P6100&oe=utf-8&client=firefox&cid=17432081723244653538&os=reviews](http://www.google.de/products/catalog?q=fujitsu+lifebook+a530+P6100&oe=utf-8&client=firefox&cid=17432081723244653538&os=reviews)

This page is written in German, I'll try to translate it:

When you have started the computer and logged in at the console:

[sudo update-rc.d -f gdm remove]
[reboot]

After it has restarted and you have logged in again:

[sudo apt-get update && sudo apt-get install linux-image-2.6.35-23-generic]
[sudo update-rc.d gdm defaults]
[reboot]

(don't type the [ ] brackets)

Please note that I can't test this myself, because I'm running ubuntu on a Medion md40100, but on my brothers fujitsu a530 this did work.:)

The webcam does work too.

---

### Post by jardo on 2011-04-02
> **seb qwertzuiop said:**
> he could solve the problem using the instructions in in the first customer review here:
[http://www.google.de/products/catalog?q=fujitsu+lifebook+a530+P6100&oe=utf-8&client=firefox&cid=17432081723244653538&os=reviews](http://www.google.de/products/catalog?q=fujitsu+lifebook+a530+P6100&oe=utf-8&client=firefox&cid=17432081723244653538&os=reviews)

This page is written in German, I'll try to translate it:

When you have started the computer and logged in at the console:

[sudo update-rc.d -f gdm remove]
[reboot]

After it has restarted and you have logged in again:

[sudo apt-get update && sudo apt-get install linux-image-2.6.35-23-generic]
[sudo update-rc.d gdm defaults]
[reboot]

(don't type the [ ] brackets)

Please note that I can't test this myself, because I'm running ubuntu on a Medion md40100, but on my brothers fujitsu a530 this did work.:)

The webcam does work too.

thanks for helping!
i'll try it and let u know how is gone

---

### Post by jardo on 2011-04-03
GREAT your instructions solved my problem.... but anyway to do what u wrote u need an internet connection!

after installation i had some problem with wifi... it has a low repeception of signal, this problem was solved by installing the ubuntu 11.04

---

### Post by beitnitzroman on 2011-09-03
Work´s fine with Ubuntu 11.04 Natty Nahrwhal netinstall. Absolutely anything is working, sound, cam, intel hd with D-Sub. Microfon is aviable but not recording. Cam screen the picture wide. In all, a nice notebook for linux users.

---

### Post by fredericd on 2012-10-26
Hello,
I got the same problem with my new AH530 as described and solved in post #12. I tried those steps but got notified that a package of the name linux-image-2.6.35-23.generic could not be found (yes, I was connected to the internet). Is it possible that the name of that file changed or something like this? What else could I try?
In case this is important: I used an old ubuntu 10.10 installation CD created last year and allowed to download recent updates during the installation process.
I hope someone has an idea what to do next... Thank you guys,
Fred

---

