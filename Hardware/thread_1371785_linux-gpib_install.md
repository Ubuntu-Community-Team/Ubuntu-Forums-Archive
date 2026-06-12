---
title: "linux-gpib install"
date: 2010-01-03
forum: Hardware
---

### Post by rdbowers on 2010-01-03
I'd like some suggestions or help with getting my shop computer working.   I'm fairly new to Linux, although I've been around computers since the early 70's.  

My shop system has an old PIII motherboard with a NI PCII/PCIIa isa 8 bit card, running Ubuntu 9.10.  I've installed linux-gpib through the synaptic installer, but it still doesn't run.

I try to use config_gpib, but get a message that dev/gpib0 isn't present.  It appears that the drivers for the cards weren't installed.  There is a tarball with the drivers, but no evidence (so far) that they were even extracted.

Also,

I plan to program in C/C++, so any suggestions for something similar to Visual C++ would be also appreciated.   I have a digitizer (Tektronics 7d20), Keithley power supply, HP DVM, and a couple of others that I will be programming.

---

### Post by grohll on 2010-03-10
Hello, I have been playing with the linux-gpib a bit, I am not sure on the ISA card as we use a usb adapter i have not messed with it in a bit but I remember having to force the driver to load and I believe you need extract them from the tar and choose the one you want. it does work though as I used ibtest to see if I was communicating ok.

if you tell me where your at with this I may be able to help


Patrick

---

### Post by thexder31 on 2010-05-06
All-

after a week of putzing around, this link was by far the best information available, and has worked now on an Ubuntu 9.10 32 and 64 bit install.  

[http://osdir.com/ml/linux.hardware.gpib.general/2008-02/msg00001.html](http://osdir.com/ml/linux.hardware.gpib.general/2008-02/msg00001.html)

I'm putting the text here, not to take credit, but to ensure that this information lives on indefinitely.  I would bet this can be adapted for the PCI card as well, but I do not know yet.  I'm using the USB card as outlined below.

[INDENT]Hi,

    I just pieced together configuring the Agilent 82357B for Ubuntu Linux, and though I would drop the recipe on the mailing list in case other want an example:

linux-gpib and the Agilent 82357B USB device

    * install the linux-gpib from source using configure, make, make install ([http://sourceforge.net/project/showfiles.php?group_id=42378](http://sourceforge.net/project/showfiles.php?group_id=42378))
    * install the firmware for usb devices (/usr/share/usb/agilent_8237a/measat_releaseX1.8.hex ([http://linux-gpib.sourceforge.net/firmware/](http://linux-gpib.sourceforge.net/firmware/))
    * plug in the usb dongle
          o for reasons I do not yet understand, it does not automatically load the firmware - I suspect an Ubuntu quirk
    * type "lsusb" to figure out which device it is
    * sudo fxload -t fx2 -D /prod/bus/usb/001/002 -I /usr/share/usb/agilent_8237a/measat_releaseX1.8.hex
          o in Ubunty, it's under /dev/bus/usb/..., rather then /proc/bus/usb/...
    * do it a second time, all the lights should go on, you will probably need to increment the usb device number
          o sudo fxload -t fx2 -D /prod/bus/usb/001/003 -I /usr/share/usb/agilent_8237a/measat_releaseX1.8.hex
    * edit /etc/gpib.confinterface{

         minor = 0
         board_type = "agilent_82357a"
         master = yes
         pad = 0
         sad = 0
         timeout = T3s
      }
          

    * execute "sudo gpib_config"
          o only the ready light should now be on
    * execute "sudo ibtest" to test it out[/INDENT]

---

### Post by rdbowers on 2010-05-31
I appreciate all of the replies, but unfortunately I lost all of my electronic equipment and GPIB boards in a fire about six weeks ago (total loss, no insurance).  I've been too busy to think about it.

I'm asking that this thread be marked closed.  Thanks for the attempts to help.

---

### Post by Jbike on 2012-11-14
It was a good move to put this stuff in a place where it would not get lost, and where other people can find it.  My first look at this lead me to the NI visa driver, but I cannot get that to install correctly (I am writing my programs with python, and was going to use the pyvisa module). I didn't have any problems installing linux-gpib but honestly do not know what "code" to use in python to access the driver. I will now take a look at the suggestions above and I will reply back if I am successful. If anyone else knows how to get gpib communiations working with python and Ubuntu I'm all ears!

Thanks,Jbike

---

