---
title: "Touch-pad doesn't respond during start up"
date: 2009-02-06
forum: Hardware
---

### Post by bulls_eye on 2009-02-06
Hi,

I have a Lenovo y-500  laptop and i have installed Ubuntu as a software inside windows .

This makes the start-up of Ubuntu rather slow.

Moreover to make matters worse my touch pad doesn't work during startup.

Thus when I have to enter my user name and password to log in to Ubuntu I face difficulty and I have to reboot every time this happens.

This process is really irritating.

Any help will be greatly valued.

Thanks.

---

### Post by neu2buntu on 2009-02-06
something similar happened me this morn on bootup (not sure why) , i resolved it by using the "fn" and in my case "f7" combination.  look for a key with a symbol that has a hand pointing inside a square on your keyboard and press it along with "fn" key....   hopefully your keyboard has such a key!!

also try "ctrl" and "alt" combination

---

### Post by bulls_eye on 2009-02-08
> **neu2buntu said:**
> something similar happened me this morn on bootup (not sure why) , i resolved it by using the "fn" and in my case "f7" combination.  look for a key with a symbol that has a hand pointing inside a square on your keyboard and press it along with "fn" key....   hopefully your keyboard has such a key!!

also try "ctrl" and "alt" combination

hmmm
i tried it....
but it didn't work out for me that way.....
i resolved it by using usb mouse and keyboard......

thanx anyway........

---

### Post by firesock on 2009-05-03
hi!

I'm having this problem too.
I'm using a dell vostro 1310 with ubuntu 9.04 (i had 8.10 and i updated it to 9.04)
The first time I start with ubuntu, none the touchpad nor the keyboard works.
I have to press the shutdown button and start again. The second time I start the machine it works perfect.
I don't know what it could be because it's weird that the first time it doesn't work and the second time it works perfect without moving anything, just restarting the machine. This is happening always.

If anyone could help me, I would appreciate so much your help.

Thank you very much

---

### Post by neu2buntu on 2009-05-03
right im looking into this problem for you now and it seems its a bug with jaunty and or a kernel update....   try this first just to confirm boot up as a restart (where your problem starts) and either keep moving the mouse , or running a keyboard key to see if it frees it up and then get back to me

---

### Post by jesse85 on 2009-05-03
I have a similar problem with my combo keyboard/touchpad for a desktop. ubuntu doesn't recognize the touchpad at all at any point. So I unplugged the touchpad part and plugged a regular mouse. That works but I prefer to use the touchpad. Unfortunately I don't have a manufacturer name for the hardware. Is there a driver somewhere? 

This has been a breaking point everytime I try Linus. If I can't use my most basic hardware, I really can't see evaluating or switching to ubuntu. Last time I just uninstalled. I hoped there was a solution or driver this time around.

---

### Post by neu2buntu on 2009-05-03
i have found this option for architecture similar to yours..... open terminal and do```
 gksu gedit /boot/grub/menu.lst
``` .then uncomment (ie remove the # ) in the kopt option .... look like this ... # kopt=root=UUID=ffefb35f-xxxx-466d-bfb0-xxxxxxxxxxxx ro and add this line to the end ```
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
``` and save the file. next in terminal run ```
sudo update-grub
``` and finally reboot to see if it works.... if it doesnt just reverse the process!!!

---

### Post by firesock on 2009-05-03
> **neu2buntu said:**
> i have found this option for architecture similar to yours..... open terminal and do```
 gksu gedit /boot/grub/menu.lst
``` .then uncomment (ie remove the # ) in the kopt option .... look like this ... # kopt=root=UUID=ffefb35f-xxxx-466d-bfb0-xxxxxxxxxxxx ro and add this line to the end ```
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
``` and save the file. next in terminal run ```
sudo update-grub
``` and finally reboot to see if it works.... if it doesnt just reverse the process!!!

Hi!

I tried this and it didn't work... :( I shutdown the machine and started it again, when I was on the login in ubuntu the touchpad didn't respond, so was the keyboard too. Both weren't responding...

So I had to restart the PC and it worked fine again after the restart.

Thank you very much for your help... if you know anything about my problem, I'll be grateful with you... 

Have a nice day...

---

### Post by ubupan on 2009-05-05
My keyboard and touch pad on my Vostro 1310 also freeze when I boot powered with the battery (obs.: I can change with the keyboard the boot options in the grub screen. It just after the post screen that keyboard and tocuh pad freeze.). With the AC power adapter, it happens randomly.

 By the way, everything was perfectly normal in Ubuntu 8.10.

  Best regards.

---

### Post by firesock on 2009-05-05
> **ubupan said:**
> My keyboard and touch pad on my Vostro 1310 also freeze when I boot powered with the battery (obs.: I can change with the keyboard the boot options in the grub screen. It just after the post screen that keyboard and tocuh pad freeze.). With the AC power adapter, it happens randomly.

 By the way, everything was perfectly normal in Ubuntu 8.10.

  Best regards.

Hi!

We got exactly the same problem... so it's a kernel bug of ubuntu 9.04, because it's happening in the same laptop model in the same way.

I have tested some solutions that i have found in the forum and in the Internet and none of these have worked.

Hope the hackers who have done such a wonderful work making Ubuntu could help us with this problem... I love ubuntu...

Best Regards

[edited]!!

Hey I have found the solution:

in the console:

gksudo gedit /boot/grub/menu.lst

In this file edit the kernel line and add in the end of this line this:
i8042.reset i8042.nomux i8042.nopnp i8042.noloop

It should look something like this:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d3383ae0-1621-4457-8138-7114fd0e3005
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d3383ae0-1621-4457-8138-7114fd0e3005 ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

Then in the kopt= line add in the end  of the line the same. It should look something like this:
# kopt=root=UUID=d3383ae0-1621-4457-8138-7114fd0e3005 ro i8042.reset i8042.nomux i8042.nopnp i8042.noloop

Then save.

With these changes, it should be working perfect at startup.

Please let me know if it worked.

Have a nice day!

---

### Post by ubupan on 2009-05-07
> **firesock said:**
> 

With these changes, it should be working perfect at startup.

Please let me know if it worked.

Have a nice day!


And yep, it worked nicely! I have made the changes that you suggested and after that executed also "sudo update-grub"

And then, I rebooted without using the AC adapter and it restarted just fine. 

Thanks again and best regards.

---

### Post by firesock on 2009-05-08
> **ubupan said:**
> And yep, it worked nicely! I have made the changes that you suggested and after that executed also "sudo update-grub"

And then, I rebooted without using the AC adapter and it restarted just fine. 

Thanks again and best regards.

You are welcome!

We are here to help, there's nothing better than helping a brother to feel comfortable with ubuntu... freedom of choice...

---

