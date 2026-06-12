---
title: "dmx4linux / Enttec USB Pro widget help?"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by dangermouse28 on 2007-10-08
Has anyone successfully installed dmx4linux and got it to work? 

I've installed it apparently without any problem but when I plug in my Enttec USB Pro box, modules are loaded, no error messages but it just doesn't do anything. Apparently the FTDI232BM chip it's based on is supported in other devices.

It's driving me nuts!

Any suggestions anyone?



Update: I've given up. After 4 years of Windows-free life I'm going to have to re-install Windows, just to get a job done. Very sad. There just isn't support for Linux in DMX control applications. Unsurprising though - there's not much demand for resource in this area.

---

### Post by albesan on 2007-11-13
hey dangermouse28,

I'm trying to do the same and finding similar problems.

I found this:
[http://www.opendmx.net/index.php/LLA_and_Q_Light_Controller_Ubuntu_Tutorial#Ubuntu](http://www.opendmx.net/index.php/LLA_and_Q_Light_Controller_Ubuntu_Tutorial#Ubuntu)

Apologies if you have already gone through it to no avail, I haven't tried it myself yet but it came up on the same search as your post so I thought I let you know.

good luck and post back if u get it working

---

### Post by albesan on 2007-11-13
ok, I run through the tutorial but I got to this command:

                  chmod a+rw /dev/dmx

and I got this:

                  chmod: cannot access `/dev/dmx': No such file or directory


Shall I just create the directory and see what happens??

---

### Post by dangermouse28 on 2007-11-14
Naw - /dev/dmx should be created by the system when you plug in your dmx box.

I gave up on dmx4linux when the developer finally admitted that the only device fully supported was a Pepperoni-type, although the website claimed compatibility with several other types (Entec included)

I've found magicq ([www.chamsys.de](www.chamsys.de)) and I'll try it when I get a free 1/2 day - they claim it's fully compatible with Entec USB Pro.

Let me know how you get on with OpenDMX - Good Luck!

---

### Post by albesan on 2007-11-14
thanks,

yes, I thought so. Looking in /dev I found a /dmx0 directory. ??

I'll give magicq a go, thanks for the tip.

a.

---

### Post by albesan on 2007-11-14
aww I thought magicq was linux based...

it is linux too, my bad.

a.

---

### Post by albesan on 2007-11-15
> **dangermouse28 said:**
> Naw - /dev/dmx should be created by the system when you plug in your dmx box.

I gave up on dmx4linux when the developer finally admitted that the only device fully supported was a Pepperoni-type, although the website claimed compatibility with several other types (Entec included)

I've found magicq ([www.chamsys.de](www.chamsys.de)) and I'll try it when I get a free 1/2 day - they claim it's fully compatible with Entec USB Pro.

Let me know how you get on with OpenDMX - Good Luck!

Hey there, 

I've given up on Qlight and LLA.

Magicq is looking good, so far so good.
There is something though, you were right /dev/dmx is created when the usb interface is plugged in, only in my system is /dev/dmx0 , any ideas why?

Also, I don't know if you ever installed Synce, but the ipaq and usbserial drivers are a real pain in the neck, I tried blacklisting them alias-ing them as off and ended up hunting them down and deleting them. I'm starting to think that's why I was having so many issues.

I'm hoping to test magicq with a full rig soon, maybe today, I'll let you know how it goes.

a.

---

### Post by dangermouse28 on 2007-11-15
Check out the installation instructions - they give a good idea of what needs removed / reinstalled - the fdti library is a good pointer. When I was trying dmx4linux and Qlight there was definitely something wrong with the kernel-supplied fdti drivers. Maybe if I'd installed libfdti it would have been different....

I've forgotten most of what I once knew about device handling but I reckon /dev/dmx0 is probably a product of a newer kernel/hal/dbus combination. Try using it as instructed for /dev/dmx.

I installed MagicQ last night - looks good but ran out of time to hook up the USB box and lights to try. Hopefully tonight!

Let me know how you get on.

---

### Post by albesan on 2007-11-15
> **dangermouse28 said:**
> Check out the installation instructions - they give a good idea of what needs removed / reinstalled - the fdti library is a good pointer. When I was trying dmx4linux and Qlight there was definitely something wrong with the kernel-supplied fdti drivers. Maybe if I'd installed libfdti it would have been different....

I've forgotten most of what I once knew about device handling but I reckon /dev/dmx0 is probably a product of a newer kernel/hal/dbus combination. Try using it as instructed for /dev/dmx.

I installed MagicQ last night - looks good but ran out of time to hook up the USB box and lights to try. Hopefully tonight!

Let me know how you get on.

Hey,

I did follow the installation instructions and seemed fine but no joy (that's for Qlight)

I tried magicq today but without success. The program runs and seems to do everything it is supposed to.
I can select the enttec pro as output, it doesn't complain about anything.
dmesg shows the usb widget and it is using the right driver. ipaq and usbserial or any other drivers are not present but I still couldn't talk to the dimmers.

I've been through the manual but it is really oriented towards chamsys hardware, so there isn't much there about how to use it with the enttec pro.

It is a pitty because I don't own any dmx equipment and I wont get another shot at a proper test for a while.

so that's it for now, I'll keep you posted on any progress, whenever it happens. I guess I'll have to get the cheapest dmx device I can find so I can test it at home.

a.

---

### Post by stevyrey on 2007-11-15
Hi all

I was having the same problem with using my dmx pro with magicq and hoary and have managed to get it sorted.

If I did a
```
dmesg
```

The last lines it reported were
```
[ 2657.204000] usb 3-1: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
[ 2657.212000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2657.216000] ftdi_sio 3-1:1.0: device disconnected

```

It seems you have to uninstall the "brltty" package as i seems to dislike the usb serial type stuff.

```
sudo apt-get remove brltty
```

Now I get
```
[ 3735.884000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 3736.064000] usb 3-1: configuration #1 chosen from 1 choice
[ 3736.068000] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[ 3736.068000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 3736.068000] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0

```

Next i started MagicQ and the little led on the back of the widget started flashing when the correct output device was chosen in the "DMX I/O" settings page.

---

### Post by dangermouse28 on 2007-11-16
I've got MagicQ working on Gutsy with an Enntec USB Pro box - needed to remove the kernel fdti module and the brltty package.

As soon as you start MagicQ, the little green LED on the Enntec box starts flashing showing that comms have been established.

I'm using Kam LED parcans so I had to create a new head, plug in all the info (name, id, channels etc) and then patch it - not sure what I patched it to but the can suddenly burst into life. I've managed to alter the data being sent using the channel testing function but that's as far as I got.

The hardest thing is actually learning how to use MagicQ. The software is a direct copy / emulation of their hardware consoles so I'm hoping the info on their consoles will give me enough to figure out how to use the thing. It's really not user friendly at all but as the blurb says - designed by lighting engineers for lighting engineers. I guess that's the problem.....

---

### Post by albesan on 2007-11-16
> **dangermouse28 said:**
> I've got MagicQ working on Gutsy with an Enntec USB Pro box - needed to remove the kernel fdti module and the brltty package.

As soon as you start MagicQ, the little green LED on the Enntec box starts flashing showing that comms have been established.

I'm using Kam LED parcans so I had to create a new head, plug in all the info (name, id, channels etc) and then patch it - not sure what I patched it to but the can suddenly burst into life. I've managed to alter the data being sent using the channel testing function but that's as far as I got.

The hardest thing is actually learning how to use MagicQ. The software is a direct copy / emulation of their hardware consoles so I'm hoping the info on their consoles will give me enough to figure out how to use the thing. It's really not user friendly at all but as the blurb says - designed by lighting engineers for lighting engineers. I guess that's the problem.....

well, that's great to know that some people got it working.

How did you go about removing the kernel's fdti module? Did install a different fdti library/module from somewhere else?

thanks

---

### Post by dangermouse28 on 2007-11-16
Follow the downloadable linux installation instructions and you'll be fine!

Plug in the box and do lsmod. Remove the kernel modules listed in the instructions. Then install libfdti using Synapticand remove the brltty stuff. Plugging in the box after that showed it connected to ttyusb0 (I think)

Start up MagicQ and you should see the green LED flashing.

Let me know how you get on - I'll help if I can.

---

### Post by dangermouse28 on 2008-01-16
After all the hassle getting the blasted thing working, I've finally given up. MagicQ is impossible to use. I've used a lot of different software packages in my time but I have to say it's one of the worst, un-intuitive, user-unfriendly pieces of crap I've ever come across.

As there's no other working alternative in Linux, I'll have to re-install XP and try out some of the Windows software available to get the job done.

Bugger.

---

### Post by albesan on 2008-01-20
well it is a pity, with all the move from dmx to ip addressing it would make perfect sense to have a linux based piece of software to control lighting...

---

### Post by enigma32 on 2008-02-26
I have confirmed the same process to get the Pro box working with MagicQ, though I haven't actually tested the output yet...

Does anyone know of a code sample using libftdi on linux?
I have tried to get the box to tell me its serial number with no success...
(everything seems ok and I write the command to return the serial number but wait infinitely on the response... not sure what I'm doing wrong)

---

### Post by enigma32 on 2008-03-01
...Turns out I can talk to the widget just fine with the ftdi-sio kernel module.

Works great as a matter of fact.
I just wish it were as easy as libftdi :-)

---

### Post by lextrax77 on 2008-04-26
hi all,

since i a ubuntu user for now 3 days, but light engineer for quite a few years, here is my way how i got the enttec dmx-usb pro up and running...

fist plugged in the interface, did dmesg and it showed the ftdi_sio and the usbserial-process running. uninstalled both like mentioned in the chamsys-howto. then uninstalled the kernel-ftdi and installed the libftdi via the synaptic-console...

afterwards i blacklisted the ftdi_sio and usbserial processes via "sudo gedit /etc/modprobe.d/blacklist"

nothing happened, no errors, but the interface didn't react to chamsys (which in my opinion is the most advanced lighting control software avaliable globally, but you have to work trough the manual)...

searched the internet, found nothing and thougt about switching to windows...

finally i ended up allowing the ftdi_sio and only blacklisting the usbserial-process!

maybe someone has the same troubles and this would help!

best regards, lextrax77

---

### Post by albesan on 2008-04-27
Hello team,

Well, thanks to everybody posting on this subject, I don't know exactly how but I managed to get the entec usb pro green light flashing indicating comunication between magicq and the usb interface.

I lost track of what actually was done to my system, I know for sure that I removed the britty packege and installed the libfti from synapctic.

dmesg tells me:

[   15.052000] usbcore: registered new interface driver usbserial
[   15.056000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   15.056000] usbcore: registered new interface driver usbserial_generic
[   15.056000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   15.092000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI USB Serial Device
[   15.092000] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[   15.092000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ftdi_sio.c: Detected FT232RL
[   15.092000] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   15.092000] usbcore: registered new interface driver ftdi_sio
[   15.092000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ftdi_sio.c: v1.4.3:USB FTDI Serial Converters Driver

I didn't blacklist ftdi_sio nor the usbserial processes.

I know this is vague, but I'm not very good at this.

I haven't been able to test it with a dmx controlled device yet but will post as soon as I get the chance to do so.

regards 

a.

---

### Post by albesan on 2008-04-28
hello team,

me again,

I was just thinking that is great to see there are a few people trying to operate lights using ubuntu and I was wondering if any of you guys intend to use it for theatre  as I am trying to.

If so it would be great to make a how to make a show with ubuntu+magicq from scratch.
I have been looking at the chamsys manual and it is a bit dense. (on top of me being a bit thick :) )
If anybody understands it better and can extract the basic steps for the creation/operation of a show would be great.
I'll keep reading the manual and trying to do this myself but my access to dmx controlled dimmers is quite limited and my progress will be slow. So it would be great if someone beat me to it :)

Anyway will post anything to this thread.

regards

a.

---

### Post by lextrax77 on 2008-05-26
hi albesan

how could i help you with the chamsys-software?
i´m really deep into it, as i use it for any kind of lightshow i do. 
mostly live applications, but also for work in bars and clubs.

pm me, we´ll solve your problems....

greets from vienna, lextrax77

---

### Post by poespas on 2008-06-08
Hello everybody,

I followed the instructions on the page Albesan
is pointing to ([http://www.opendmx.net/index.php/LLA...utorial#Ubuntu](http://www.opendmx.net/index.php/LLA...utorial#Ubuntu)).

Everything went fine until I initaite the command :
"llad -d 3 -f -s"

This is the output of the command :

Failed to open lla-universes.conf:  No such file or directory
Loaded plugin SandNet Plugin
Loaded plugin EspNet Plugin
Loaded plugin ArtNet Plugin
Loaded plugin ShowNet Plugin
Loaded plugin UsbPro Plugin
Loaded plugin OpenDmx Plugin
Loaded plugin Pathport Plugin
Loaded plugin StageProfi Plugin
Loaded plugin Dummy Plugin
Trying to start SandNet Plugin
Registered fd 3
Registered fd 4
Installed device
Started SandNet Plugin
Trying to start EspNet Plugin
Registered fd 5
Installed device
Started EspNet Plugin
Trying to start ArtNet Plugin
Failed to open lla-artnet.conf:  No such file or directory
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Afgebroken (core dumped)

Anybody any idea how I can resolve this problem ?

Best regards,

Bruno

---

### Post by poespas on 2008-06-08
Addition : I have a "/dev/dmx0" device
in stead of the "/dev/dmx" device as used in the tutorial.

Can that be a reason for my problem ?

Bruno

---

### Post by albesan on 2008-06-08
hey bruno,

I had similar issues, I never got to the bottom of it but if you read page one on this thread some people offered some advice on why you get this /dev/dmx0 instead of just /dev/dmx.

I gave up on lls and moved to chamsys magicq, still trying to work it out properly but at least I managed to get it to talk to the usb dmxpro widget.
It is just a bit hard to get to know but some of the people posting on this thread have been really helpful.

Regards.

a.

---

### Post by poespas on 2008-06-13
Hello All,

Is there anyone having a working solution on dmx ?

You suggestions are welcome.
Any pointers to resources on the net ?
Forum ?

I did a new try last night, without succes.

Regards,

Bruno

---

### Post by albesan on 2008-06-13
hey bruno.
have checked the chamsys qlight?
Seems to work on feisty

regards.

a.

---

### Post by poespas on 2008-06-14
Hi Albesan,

Doesn't this application needs dmx4linux or lla ?

Does it have its own drivers ?

Bruno

---

### Post by albesan on 2008-06-14
hey Bruno,
It doesn't need LLA. 
I'm not sure exactly how it works, but it does.
Take a look at the software documentation, it'll be explained there.
There are some issues with the ftdi drivers but they seem to have been fixed.
Again read through this thread, mine and others experiences with qlight are documented there.

I hope this helps. Sorry to be so vague but it's been a while since I installed it.

a.

---

### Post by poespas on 2008-06-16
Hi There,

Yesterdag I have tried your suggestion, but as dangermouse 
already said, it is very contr-intuitive to use and
very console-oriented.  It is no fun using it.

I'm getting disapointed.  I'm thinking of running
Freestyler under wine.

I find it very regrettably that I can't get it to work.

It seems all active development on the relevant
projects (dmx4linux, dmx usb from Erwin Rol, lla, qlc, ...)
has stopped a year or 2 ago.

If I only had more experience in C programming.

Regards,

Bruno

---

