---
title: "Ubuntu 10.10: suspend and hibernation not working on sony vaio vgn-fw21e"
date: 2010-11-06
forum: Hardware
---

### Post by LtPitt on 2010-11-06
Hello dear friends!

1st: my kernel data...
Linux version 2.6.35-22-generic-pae (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010


I've just installed maverick everywhere (almost including the fridge and the oven :D) and the only little problem I have is on my vaio.
After a fresh install, when I close it, it looks like going in suspend mode but when I open and try to wake it up it just boots like I've turned it off.
Same thing happening for hibernation...
I've tried a suggestion that was in Maverick release notes:

> When the XHCI module is loaded for USB 3.0 operation the system cannot suspend. Manually unloading XHCI will allow suspend to complete normally. To avoid future suspend problems, the workaround is to add SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module then the system can suspend normally.




Without luck: it still doesn't work in the way I've described before.
Can anyone help me to understand what is not working?
Even a suggestion about which logs to check would be awesome.

Fair thanks to anybody who made Ubuntu possible :)

---

### Post by LtPitt on 2010-11-06
ps

hold on: i was incorrect!

To complete the troubleshooting hibernating works great...
It's just suspend not working...

---

### Post by bhavya juneja on 2010-11-17
I am having a similar problem. But my hibernation is also not working properly.
Please don't forget to post if you find the solution.

---

### Post by vanlindholm on 2010-11-21
Great stuff this also worked on my vaio VPCF13Z1E/B.

---

### Post by kardain on 2010-11-22
Fixed suspend and hibernate on my ASUS AT5IONT-I motherboard (running Maverick x86). Nice find, thanks!

---

### Post by lenu on 2010-12-09
so, the workaround adding SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module is the solution after all?

also, could someone with the vaio vpcf13z1e/b confirm which functions (if any) are currently not working in maverick?

---

### Post by mike1323 on 2010-12-12
[I][B]
It didn't work on the next day! 

[/B]Make sure [/I]* 'acpitool' i**s installed*:
 *Synaptic Package Manager ( install 'acpitool')*
            [I]                 or
sudo apt-get install acpitool[/I] .
   
[I]Than run
sudo acpitool -s [/I]
          *   or*
 *suspend your system like regularly.*

[I]It works for &#8220;Toshiba Satellite L355&#8221;. 
[/I]
*it's from the source:*
                   [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1606478&page=3](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1606478&page=3)

---

### Post by hubrat on 2011-01-11
Thanks, suspend now works for me on my Asus P7H55-M/USB3 motherboard.

---

### Post by poodlefluids on 2011-01-29
> **hubrat said:**
> Thanks, suspend now works for me on my Asus P7H55-M/USB3 motherboard.

Just wanted to put it out there that installing acpitool and adding SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module worked for me on a Sager NP8690 (modified Clevo W860CU).


Torben

---

### Post by twak on 2011-01-30
This also fixed suspend on my "Gigabyte GA-X58A-UD3R Intel X58".

> add SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module 

I had to create the file unload_module and add the line.

---

### Post by potted_meat on 2011-02-13
This fix also worked on my Lenovo ThinkPad W510.

---

### Post by kiruri on 2011-02-26
I confirm that this solution works with the following configuration:

Lenovo Thinkpad w510 (Intel i5 processor), Ubuntu 10.10.

---

### Post by fjgaude on 2011-02-26
This fix (adding a line in newly created file, unload_module, to /etc/pm/config.d) worked for my i5 Intel box with USB3 features. It seems that Ubuntu 10.10 handles USB3 and that creates the suspend issue. In 11.04 adding that file with the line suggested in the Release notes is not necessary. They didn't just add the line the way we do in 10.10.

If memory serves me I don't think 10.04 would even boot the i5 MB with USB3 capability.

---

### Post by thorbjornw on 2011-04-20
I had the same suspend problems on Ubuntu 10.10 with both my stationary PC (Intel motherboard) and my Vaio VGN SZ750 laptop (both worked fine on 10.04). On the stationary, the problem could be solved by installing uswsusp, but this slows down the boot. After some search on the net I found the following solution:

Create the file /etc/pm/config.d/unload_module

and insert the line:

SUSPEND_MODULES="tpm_tis"

Now both machines suspend correctly with no need for uswsusp.

The alternative is to blacklist the module (which also works), but I understand it is not the best solution as the module has some useful functions related to security.

---

### Post by yrraja on 2011-04-20
It worked for Lenove ThinkPad T500

I inserted following line to /etc/pm/config.d/unload_module:
SUSPEND_MODULES="xhci-hcd"

Rebooted the machine. Suspend works fine now.

Thanks

---

### Post by robincoghlan@gmail.com on 2011-04-28
> **twak said:**
> This also fixed suspend on my "Gigabyte GA-X58A-UD3R Intel X58".



I had to create the file unload_module and add the line.
Hi, am new to Linux (about 6 weeks) and getting on nicely with it. Suspending my pc is the only issue I have. 
Please explain how you created the unload_module file - what format? 
Is it as simple as adding only the text - SUSPEND_MODULES="xhci-hcd" - and nothing else? 

FYI when I tried saving a file to this location a message came up saying I do not have access rights?

Help would be much appreciated. Thanks

---

### Post by hjhk on 2011-05-16
Thanks! This solution solved my problem of suspend!:)

@ robin
you need to have the permission to save that file.
do this

cd /etc/pm
then,
chmod a+rw config.d

after doing this try saving the file again. It should work now.

---

### Post by TedinOz on 2011-07-20
> **thorbjornw said:**
> I had the same suspend problems on Ubuntu 10.10 with both my stationary PC (Intel motherboard) and my Vaio VGN SZ750 laptop (both worked fine on 10.04). On the stationary, the problem could be solved by installing uswsusp, but this slows down the boot. After some search on the net I found the following solution:

[HTML]Create the file /etc/pm/config.d/unload_module[/HTML]

and insert the line:

SUSPEND_MODULES="tpm_tis"

Now both machines suspend correctly with no need for uswsusp.

The alternative is to blacklist the module (which also works), but I understand it is not the best solution as the module has some useful functions related to security.

I know this is a while since these discussions but I am hoping someone will be able to help me with this. I have always been able to use suspend but for the past couple of days it has stopped working...it takes me to the log off which then disappears and I have a black screen with backlight (as described by others here) but my only option is to hit the power button and re-start. I normally don't use Hibernate but have just tested it and the same thing happens. One thing I have noticed is that every time I restart by this method the sound icon in the indicator panel has started in 'mute'...whether this is connected to the problem I am not sure.

The solution within here seems to have worked for many but my problem is that I don't know how to```
Create the file /etc/pm/config.d/unload_module
```. When I paste this to the Terminal I am told ```
bash: /etc/pm/config.d/unload_module: No such file or directory
```

As an inexperienced user if someone can help me achieve this I will greatly appreciate it.

Thanks in Adv.

---

### Post by TedinOz on 2011-07-21
Update:
Ok I think I have figured some things out now even though no success yet. I found this link which showed me how to create and save etc. files [http://ubuntuforums.org/archive/index.php/t-800128.html](http://ubuntuforums.org/archive/index.php/t-800128.html)

Following this I was able to create the file /etc/pm/config.d/unload_module:
( is the : at the end to be part of the file name?)
I did this twice, first using...SUSPEND_MODULES="tpm_tis" and then...SUSPEND_MODULES="xhci-hcd". I did both of these steps separately and re-booted each time after Save but regret that so far [COLOR="Red"]SUSPEND[/COLOR] still does not work.

Have I done things correctly and if so is there anything else I can do?

My laptop is Toshiba L300 and am running kernel 2.6.36.

I am happy to provide any log file info if told what is needed.

All help will be appreciated. Thx

---

### Post by TedinOz on 2011-07-21
A further update.

I eventually realised that this problem began only since I had upgraded Virtual Box from version 4.0 to 4.1 a couple of days ago so I have now uninstalled Virtual Box and SUSPEND and HIBERNATE are both now working perfectly. I have no idea what has caused this and couldn't find anything in VB to indicate a problem and that system seemed to working fine but the uninstall has resolved it. I am yet to re-install VB but if when I do the problem re-occurs I will report it here...maybe it can be part of a solution for someone else who is more 'in the know' than I am.

---

### Post by wakysr on 2011-11-10
this fix worked for me, thanks a lot
Ubuntu 10.10 on Asus A53S,Intel i5, nVidia GT540M

---

