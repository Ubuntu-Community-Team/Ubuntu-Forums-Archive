---
title: "Controlling Lights"
date: 2008-06-16
forum: Hardware
---

### Post by billynomates on 2008-06-16
Is there anyway I can control the lights on the front of my PC? I know about blink for controlling the scroll/num lock lights, but I would like to turn off the power lights etc.

I've tried Googling to no avail.

Thanks in advance!

---

### Post by mrtomservo on 2008-06-16
I'm not aware of any way to do this.  However, you might want to look into controlling LED's with your parallel port.  I have a setup so that one led indicates power on, the second controls the LED backlight of it's LCD monitor, the third shows HDD activity, and the forth shows me when I have new email.  They can be turned on or off by running simple scripts I made.  I can provide some more information if you're interested.

Hope that helps a bit.

---

### Post by sdennie on 2008-06-16
You *might* be able to do this with xset.  Just type xset in a terminal to see the available options for doing this.

---

### Post by billynomates on 2008-06-30
> **mrtomservo said:**
> I'm not aware of any way to do this.  However, you might want to look into controlling LED's with your parallel port.  I have a setup so that one led indicates power on, the second controls the LED backlight of it's LCD monitor, the third shows HDD activity, and the forth shows me when I have new email.  They can be turned on or off by running simple scripts I made.  I can provide some more information if you're interested.

Hope that helps a bit.

Yeah, that sounds interesting. That's pretty much exactly what I want to do: have my on/off light blink when I get an email. At the moment I've just got my scroll lock light blinking. It'd be great if you could provide some further information!

---

### Post by mrtomservo on 2008-06-30
Excellent!  Here's the basics of what I did.  I can try and elaborate on any step if need be.  It's fairly tedious, and frankly after typing this up i'm left wondering if there isn't an easier way to do this.  Any suggestions are **welcomed**!  It will require a basic understanding of scripting, electronics (LED's), and relies entirely on the terminal.

1. Download the parport led driver.  You can find it here:
[http://code.bastart.eu.org.nyud.net/files/leds-parport-0.0.1.tar.gz]("http://code.bastart.eu.org.nyud.net/files/leds-parport-0.0.1.tar.gz")
Put it in a location that you can find later, I use */home/username/source/*.

2. Make sure you've got your system setup to compile code, you may need to install kernel-headers, make, etc - if you get an error message while trying to compile.  

3. Uncompress the tar file by either using the GUI tool, or in a terminal:
```
tar xvf leds-parport-0.0.1.tar.gz
```
in the directory where the driver is.

4. As root, we'll next compile the drivers, copy them, run depmod, and modprobe. You can use sudo or become root via su.  Enter the directory where you untarred the driver.  Then:
```
make
``` 
then copy the driver to the proper location:
```
cp leds-parport.ko /lib/modules/`uname -r`/kernel/drivers/leds/
```
then run:
```
depmod -ae
```

Edit your /etc/modules file so that "lp" won't get in the way, and so that "leds-parport" loads at boot:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
#lp  <-- disabled to prevent clashing with leds-parport
leds-parport

You'll want to reboot and then check that the install has gone properly.
```
ls -alh /sys/class/leds/
```

You should see a list something like this:
> total 0
drwxr-xr-x 10 root root 0 2008-06-30 20:52 .
drwxr-xr-x 28 root root 0 2008-06-30 20:53 ..
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led1
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led2
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led3
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led4
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led5
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led6
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led7
drwxr-xr-x  2 root root 0 2008-06-30 20:52 parled:led8

Done with the install, now to set it up.  I'm sure the way i've gone about this is sloppy and there's bound to be a better way, so please if anyone would chime in and clean it up.  

You probably won't have permissions to change the led state.  So you'll want to make a script to run at boot, or you can do this manually, it's up to you.  But essentially you'll want to change the permissions for the leds.  This is the script I use, let's call it "activateleds".  Make sure to make it executable via "chmod +x filename".

```
#!/bin/bash
#changing permissions so I can write to their config files
sudo chmod -R 777 /sys/class/leds
#complete.
ls -alh /sys/class/leds
echo Permissions changed, ready to go!
```

I saved it to /etc/init.d/, and ran as root:
```
update-rc.d activateleds defaults 99
```

Now it will automatically run at all runlevels.  It's not needed when you shutdown, and I don't remember the syntax for selecting certain runlevels and not others, so I just manually removed any links it created in /etc/rcx.d/K99activateleds.  IE, runlevels rc0.d, rc1.d, rc6.d.  

To change the state of led 1 to ON you'll want to type:
```
echo 1 > /sys/class/leds/parled\:led1/brightness
```
To turn it off change the echo from 1 to 0.
Obviously, you probably don't want to type this out everytime.  So I made a script called led1on and led1off respectively.  For example:

> #!/bin/bash
#turns led 1 on, if you haven't - run activateleds first!
echo 1 > /sys/class/leds/parled\:led1/brightness


Technically I think you can control 8 leds with this setup.  Personally, i've only gotten 5 or 6 to work.

You'll have to look up which pins go to what on a parallel cable, I've found that mine are almost always different.  You can find some pinouts searching on Google or the like.  I had to figure out which was which by trial and error.  If you use a regular led make sure you include a resistor if you care about the led's longevity.

The computer I run the leds from is a server on my lan.  It's an old 450 mhz that gets left on all the time.  It's a Debian terminal, and as such I don't use a gui email client, I use fetchmail/ssmtp/mutt.  As such, I was able to write a script that checks the errorlevel output of fetchmail.  The script I use is: (you'll want to edit the directories to where your scripts are located, and whatnot.)

> 
#!/bin/bash
# flash led if new email
PATH=/home/servo/scripts
/usr/bin/fetchmail -k
if [ $? -eq 0 ];
    then echo error level zero - activating led!|/home/servo/scripts/led2on
elif [ $? -eq 1 ];
    then echo error level one - no new mail
fi


So I guess that's it for now.  Best of luck if you decide to try this out.  I have this thread on notify so i'll reply back whenever I can.

---

### Post by billynomates on 2008-07-05
Wow, thanks so much for writing all that out!
Everything works great, except that when I 
```
ls -alh /sys/class/leds/
```
all I get is this:
```
drwxrwxrwx  2 root root 0 2008-07-05 18:02 .
drwxr-xr-x 38 root root 0 2008-07-05 18:02 ..
```

Does this mean it's not aware of any leds, or do I need to write something in there myself?

---

### Post by mrtomservo on 2008-07-05
Hey, no problem!  Glad to help.  I had the same problem with the directory being empty when I tried to install in on both my Ubuntu boxes.  (8.04 and 7.10)  So anywho, I narrowed it down to being a problem with another driver hogging the printer port.  That's why I had the steps about editing the /etc/modules file to comment out the lp driver.  My guess would be that you have some driver interfering with the leds-parport.  Could you try posting your /etc/modules file, and the output from the following commands?

```
lsmod | grep parport
```
```
dmesg | grep parport
```

---

### Post by billynomates on 2008-07-11
Hey, sorry for the delay

> mike@speedbuntu:~$ lsmod | grep parport
parport_pc             41128  0 
leds_parport            9624  0 
led_class               7176  1 leds_parport
parport                44300  4 ppdev,lp,parport_pc,leds_parport


mike@speedbuntu:~$ dmesg | grep parport
[   52.137959] parport-led: parallel port does not exist
mike@speedbuntu:~$ 


---

### Post by mrtomservo on 2008-07-12
Seems like your parallel port isn't being found by the kernel.  Are you sure that you've got it enabled in the bios?

---

### Post by billynomates on 2008-07-22
Yeah, pretty sure. :confused:

---

### Post by mrtomservo on 2008-07-25
Hmmm.  I remember once someone stating the reason they couldn't get a module to load was because of the order they were loaded.  On all my machines it says:

parport                37832  4 ppdev,lp,***leds_parport,parport_pc***

I noticed yours has parport_pc before leds_parport.  Could you post your /etc/modules file?  
Maybe there's something funky in there.

---

