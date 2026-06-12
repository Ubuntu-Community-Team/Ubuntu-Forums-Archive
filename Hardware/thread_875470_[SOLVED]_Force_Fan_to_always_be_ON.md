---
title: "[SOLVED] Force Fan to always be ON"
date: 2008-07-30
forum: Hardware
---

### Post by vandorjw on 2008-07-30
My laptop runs too hot.

I have tried many things to try and make it run cooler.
I want a way to force my cooling fans to always be on, no matter what temp the CPU is. HOW do I do this?

Please, don't tell me I don't need this...

Just tell me how to do it.

Thanks in Advance - CC7

---

### Post by Daelyn on 2008-07-31
> **cc7gir said:**
> My laptop runs too hot.

I have tried many things to try and make it run cooler.
I want a way to force my cooling fans to always be on, no matter what temp the CPU is. HOW do I do this?

Please, don't tell me I don't need this...

Just tell me how to do it.

Thanks in Advance - CC7


There is no way "just how to do it"!!

Make/manufacturer, model of laptop etc. would be a benefit.
We ain't psychics here, mate.

---

### Post by BluePlum on 2008-07-31
> **Daelyn said:**
> There is no way "just how to do it"!!

Make/manufacturer, model of laptop etc. would be a benefit.
We ain't psychics here, mate.

I am watch...

Your name begins with a.... Letter in the alphabet... 
Your wearing a Shirt with a.... Colour on it.

Am i right?

Yeah about the fans we need models etc..

---

### Post by vandorjw on 2008-07-31
I did not mean to be rude, and looking back, I hope I didn't come across that way.

I have a Dell Inspiron 1520

**Procesor**: Intel T7500 @2.2GHz 4MB cache 
**Ram**: 2GB @ 667mhz
**GPU**:NVidia GeForce 8600M GT
[INDENT][/INDENT]Vbios Version: 60.84.50.00.02
[INDENT][/INDENT]Memory: 512 MB

I believe that this is the type of fan.
DELL INSPIRON 1520 COOLING FAN E233037
(I am not 100% sure if this is correct, I just google searched till I found something that seemed right)

I can give the "Original System Configuration" list if that is helpful at all. However, it uses a lot of short forms and I do not know what half the items represent.

Hope it helps - CC7

---

### Post by linux_tech on 2008-07-31
A while back I was a field support engineer for Dell, Gateway, Lenovo.  When I was sent out to resolve these types of issues, usually replacing the system 
board, fan, heatsink, and/or cpu resolve overheating issues.

The number one cause of over heating w/ laptops I found was that the heat sink has become clogged with dust, cat fur , etc.  Usually dis-assembling the laptop to the the point necessary to access the heatsink cooling fins and cleaning them out with some air works great!

You can also re-apply new thermal grease between the cpu and heatsink. 
This won't hurt anything.

If the laptop is still over heating, then you can find some software that will monitor the thermal temp of the cpu and turn on the fan high speed when the cpu heats up to a certain temp.

For linux you can try this laptop fan regulator for Linux/Solaris:
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/) 

For Windows, one to try - [http://www.diefer.de/i8kfan/](http://www.diefer.de/i8kfan/)

suggest Google search for Dell fan utility

---

### Post by vandorjw on 2008-07-31
Thank you, almost excactly what I was looking for.

linux_tech, THANK YOU soo much!
After I installed DellFand, I can actually HEAR the Fan blowing again when my Laptop reaches 50 Celcius! :)

Never before in Ubuntu have I HEARD the fan going. I did in windows.

I hope someone takes this application and develops it, so it is not only for the Dell's anymore, and include it standard in Ubuntu, Kubuntu, Xubuntu installations.

---

### Post by vandorjw on 2008-08-01
Is there a way to make the fan stay on longer?
At the moment, it will run for about 1 second, turn off for a second, then run, then off, on off on off.

I wanted to see what it would do if I used burnMMX, (a heavy CPU tester)
I ran it on both cores, and within 5 seconds, my temperature went from 60 Celcius, to 85 Celcius.
It still did the same, on off on off routine at this temp, so I quickly killed the process.
I wish for the fan to continue to run until a lower temp is reached.
(Although this may not be possible)

ALso,do you have an idea what this means?

"dellfand: warning: set fan 0 status to 0 last cycle, it's now 2 (BIOS interference ?)"

I was looking throught the Source Code, and saw this.
---------------------------------------------------------------------------------------------

// Little check it got/stayed set to what we asked last time

			if ( 
				( last_set_status >= 0 ) &&
				( last_set_status != old_status )
			) {
				fprintf( stderr, "dellfand: warning: set fan 0 status to %d last cycle, it's now %d (BIOS interference ?)\n", last_set_status, old_status );
				last_set_status = -2;
			}

			// Only set fan if it's not what we already want (duh...)
			//

--------------------------------------------------------------------------------------------------
Any Idea on how I can Make "My Temp Values Stay"?


--------------------------------------

PART 2 (This is a different problem)


BIOS can no longer Detect the power input.

I have a 65w power brick, which was working fine before I started using dellfand. Now the BIOS reports I have a power failure or something of the like.

I think I need to manually shut off the "dellfand" deamon, but I don't exactly know how to do this.

My guess would be to open the terminal and type,
> 
/etc/init.d/dellfand stop


but, is there a way to have this done automatically, 
(Can I add this to the "to-do" list of shutdown things?)

I hope you understand what I mean.

Thanks - CC7

PS: I am 100% sure there is nothing wrong with my power supply, or the rest of my system. The first time I saw that error message, I had an option to do a system self check (which took an hour), and every test was passed.

---

### Post by linux_tech on 2008-08-02
I don't have a Dell inspirion 1520 handy, just a thinkpad, so I can't test 
So trial and error... Try these files and let me know the results. I'm most familariar with the i8kfan..gui utility
You probably shouldn't need to go too low, if you set it too low, then the fan will just stay on which will serve to the cpu cooler, but maybe at the cost of a fan over long term use. 

The dellfanand util I'm not sure how to run automatically but to use manual you may copy the dellfand files to usr/local/bin/ as root, then launch
# dellfand mode sleep-seconds off 20 low 40 high 50
usage: dellfand [<mode> <sleep seconds> <off> <low> <high>]"


On the bios error, I'd just reflash bios, but possibly fixing the erratic fan behavior will stabilize the fan  and maximum rpm will not occur. These are likely due to built-in/BIOS-based fan control algorithms
"dellfand: warning: set fan 0 status to 0 last cycle, it's now 2 (BIOS interference ?)" basically refers to a warning that maximum fan speed has occured

To have process stop automatically at shutdown c/dellfand stop
may work or a script in /etc/init.d may also work 
But see if you can get fan right first. 

ref links-
Fan controls for Linux
   1. A FreeBSD/NetBSD/OpenBSD version of the original DOS i8kfan command line tool ported to *BSD by Damir Lampa (unfortunately the link is dead)
   2. Since Linux kernel 2.4.15 there's also a kernel module written by Massimo Dal Zotto to get access to the important SMM functions under Linux. The tools to access that driver are here:  [http://www.debian.org/~dz/i8k/](http://www.debian.org/~dz/i8k/)
   3. Here's a daemon called dellfand specifically for the linux 2.6 kernel series: [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/) 
[http://www.diefer.de/i8kfan/manual31/index.html--](http://www.diefer.de/i8kfan/manual31/index.html--) windows but some interesting gui pics allows you to see all different fan settings
[http://vl.zuser.org/cgi/archive/man?start-stop-daemon](http://vl.zuser.org/cgi/archive/man?start-stop-daemon)
[http://packages.ubuntu.com/hardy/i8kutils](http://packages.ubuntu.com/hardy/i8kutils) - this is another one (deb pkg) to try for inspiron
[http://brainstorm.ubuntu.com/idea/9743/](http://brainstorm.ubuntu.com/idea/9743/) - more on I8kfangui

---

### Post by vandorjw on 2008-08-02
I have the latest BIOS Version for the Inspiron 1520.
My kernal Version is 2.6.19-generic, so sadly the i8kutils won't work for me.

(The read me said it was only for Kernal 2.4 and 2.5)

**Update**
I am running of battery power, and my fan now stays on for longer periods of time. Up to a minute now :guitar:

Last time, right before I shutdown, I entered the command "/etc/init.d/dellfand stop"

This morning when I booted up, my BIOS did not give me a warning.

I agree that I should enter some sort of scrip into /etc/init.d/

However, my coding skill are not so good. (I know C#, and am learning C++)

-Also, I checked out your "hacked" version of Dellfand, and the Source was no different as far as I could tell, so I haven't used it yet.


Thanks for all your help.

My heat problem is solved.

---

