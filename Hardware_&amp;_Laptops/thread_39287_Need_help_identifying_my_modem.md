---
title: "Need help identifying my modem"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by renoir98 on 2005-06-04
Hi all,
i've just installed a 56k modem given to me by a friend of mine.
My goal is to try to make it working under my Hoary installation.
The product is Trust "56k v92 pci modem" and is equipped with a 
Intel chipset.The box doesn't give other infos.
I've run the scanmodem utility but i wasn't able to figure out the
exact chipset in order to find a suitable driver.
This is the scanmodem output:
```
Providing detail for device at  0000:00:0c.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:1080   Modem: Intel Corp.: Unknown device 1080 (rev 04) (prog-if 00 [Generic])
  SubSystem 8086:1000   Intel Corp.: Unknown device 1000
0000:00:0c.0 0703: 8086:1080 (rev 04)
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:1080 8086:1000 debian 2.6.10-5-386 3.3.5 3.3.5    i686

       
 The soft modem Subsystem operates under a controller
   8086:1080 ac97 controller 				i . 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Intel
 The Subsystem PCI id does not itself identify the modem Codec.

  Driver snd-intel8x0m  may enable codec acquisition 
```
It seems to be an Intel ac97 modem.
But how can i have it working?
Which driver shall i use?
Thanks in advance.

---

### Post by renoir98 on 2005-06-04
In the meantime i've installed the Smartlink kernel modules and daemon as suggested in the unofficial guide.
At the end of installation procedure a /dev/ttySL0 should be created but this doesn't happen so the /dev/modem symlink is broken.
Any suggestion?
Am i on the right way with this driver?

---

### Post by az on 2005-06-04
If your modem is quite new, you may need a newer version of the driver.  The licencing of the driver from smartlink changed and that version cannot be distributed in the same way as the version you have.

If that is the case, you can try compiling the new version of the driver.  Get it from the smartlink website (google smartlink modem linux)  transfer the driver to your ubuntu system (by usb drive or floppy if you cannot get onto the net without your modem)


Also, install build-essential and linux-headers-2.6-5-10-386 (they are on your cd.   Just use synaptic)

then open a terminal and go to the directory where the driver tarball is and do:

cd /Desktop  # enter the directory where the driver tarball is...
tar xvzf sl*
cd sl*

make
sudo make install

Then you need to load the module you just compiled:

sudo modproble slamr

and run the modem deamon
/usr/sbin.slmodemd



From there you need to comfigure it as you would usually.  You will need to automate the process of running the deamon and loading the module.  Read the README.


By the way, are you running the stock kernel?  If you are running a non-386 kernel, that prebuilt packages for the driver are not for you.  BUt I am assuming you have no other internet access and that you can not have installed another kernel.

---

### Post by renoir98 on 2005-06-05
Thank you azz,
following your instrctions and the README file included in the driver package
i've come to a good point but still haven't it working.
Everything seems correctly installed but when i run this command
```

/usr/sbin/slmodemd --country=ITALY /dev/slamr0

```
even as root,i get these errors:
```

error: mdm setup: cannot open dev `/dev/slamr0': No such device
error: cannot setup device `/dev/slamr0'

```
But i'm sure the device /dev/slamr0 is where it should be since i see it!!!
Another conseguence of this is the error i get when i try to connect via
"pon" after configuring a new connection using pppconfig.
First I've set /dev/ttySL0 and then,after creating a symlink to it,/dev/modem;
But both are recognised as invalid options.
But i think this happens because the first problem.
Hope you can help me furtherly.
Thanks again,renoir.

PS:the slamr kernel module is also correctly loaded.

---

### Post by renoir98 on 2005-06-05
Updates:
i've discovered that the modem is equipped with a Intel 537EP chipset.
I've followed an How-to on this forum and had it installed but,i'm afraid,not
well configured.
The modem is now recognised but it outputs a
"NO DIALTONE" error when i try to connect and the connection script
is terminated.
The phone cable is correctly plugged,of course.
The readme file suggested to change the International code settings
for using the modem outside the USA and i'm in Italy so i should do this.
But it's not simple via minicom(at least for me).
Do you know how can this be done?

---

