---
title: "Laptop is overheating"
date: 2011-02-09
forum: Hardware
---

### Post by tmnuwan12 on 2011-02-09
I just installed Ubuntu to my laptop Dell inspiron 1525. I used Windows on that machine for 5 years without any overheating. I used it more than 13 hours a day every day. But when I installed Ubuntu it is shutting down automatically. I checked kernel logs and is was saying "critical temp reached 99C".

Is there any way Ubuntu can control the temp of system when it is busy..Thanks in advance.

---

### Post by P4man on 2011-02-09
Is the fan turning at all?
It could be a misreading, but more likely the CPU fan isnt working. In either case, please see the link in my signature for possible causes and solutions.

If that doesnt help, have a look here:

[http://ubuntuforums.org/showpost.php?p=9882555&postcount=14](http://ubuntuforums.org/showpost.php?p=9882555&postcount=14)

---

### Post by tmnuwan12 on 2011-02-09
> **P4man said:**
> Is the fan turning at all?
It could be a misreading, but more likely the CPU fan isnt working. In either case, please see the link in my signature for possible causes and solutions.

If that doesnt help, have a look here:

[http://ubuntuforums.org/showpost.php?p=9882555&postcount=14](http://ubuntuforums.org/showpost.php?p=9882555&postcount=14)
Thanks for your reply first of all. I appreciate it very much. Yes, The fan is fully functional. At the moment I have rescaled my cpu clock to 800Mhz(max is 1.7GHz) to reduce overheating, But I am running that manually and I am cutting back most of programmes to prevent overheating. Is there any way I can automate the system to scale back the clock speed when it is getting too warm..Please note it takes less than one hour for the system to reach the critical trip point and It is also bit wierd. All ideas wellcome.Thanks in advance..

---

### Post by SNYP40A1 on 2011-02-09
I just posted a response to this issue last night.  Find a compressed air source and blow high PSI air directly into the fan while the fan is running.  Should create a huge dust cloud.

---

### Post by psusi on 2011-02-09
Yep, clean out the dust ;)

---

### Post by P4man on 2011-02-09
Cleaning the heatsink is definately a good idea, but also do check the link in my signature, a buggy acpi bios will often incorrectly report overheating to linux, when in reality all it wants is to speed up the fan. If the fan isnt blowing full speed, then its likely not a dust problem, but a bios one. Installing lm-sensors to read CPU temps might shed more light on it.

---

### Post by aloya82 on 2011-02-09
I have a toshiba satelite M550 and it overheats everyones laptop is overheating this is not a dust issue its a bug in the os.  when i switch back to windows no overheating fan turns on just fine when i switch to ubuntu fan doesnt turn on at al and the pc overheats.  THIS IS NOT A DUST ISSUE! please stop telling people to blow out the fan because its dirty.  If you dont have any useful help dont speak.   Thanks to all the guys actually coming up with solutions ive seen several guys have fixed theirs ive yet to find a satelite fix but im working on it hopefully get something soon and ill post it. until then please stop with the BLOW OUT YOUR DUST bs please.  its annoying.

---

### Post by psusi on 2011-02-09
If the fan does not turn on, it is because your bios is broken.  Many vendors ship broken ACPI BIOS and tell you to install some BS windows software to work around the bug.

---

### Post by killfall on 2011-02-09
I know this has been said but seriously cleaning out the heat sink makes a hell of a difference. There is no need to get all angry and bent out of shape about people suggesting it. On my windows box when I first got GTA4 I couldn't get it to run without a super low framerate. But I took the heat sink out and gave it a clean and put some new heat paste on the CPU and then after that the game ran smoothly and 5 degrees colder.

The issues with shutting down is most probably a BIOS issue as when the bios reports that it is getting too hot and needs to speed the fan up Ubuntu sometimes ready it as a "Too hot must shutdown" message from certain BIOS models. 

There has been no useless advice on the thread and so please don't leave angry, rude messages as that is the only unhelpful post!!

---

### Post by tmnuwan12 on 2011-02-09
> **P4man said:**
> Cleaning the heatsink is definately a good idea, but also do check the link in my signature, a buggy acpi bios will often incorrectly report overheating to linux, when in reality all it wants is to speed up the fan. If the fan isnt blowing full speed, then its likely not a dust problem, but a bios one. Installing lm-sensors to read CPU temps might shed more light on it.

Thanks all for your replies and suggestions. I have done almost everything you guys have suggested before posting this thread. But now I am running my both cores at 800MHz to reduce the heat and it is a workaround. But it works ok for time being. I just installed this lm-sensor , but don't know how to run that app from command line. Any ideas...Thanks in advance..

---

### Post by Kirboosy on 2011-02-09
How long does the computer stay on before it overheats? (on average)

I would try just updating the BIOS (and no you can't run BIOS updates via wine)

If you can boot into Windows and apply the BIOS upgrade.

If you don't have Windows there are DOS methods and others that are a bit trickier.

[How to Flash BIOS]("http://ubuntuforums.org/showthread.php?t=318789")


[aloya82]("http://ubuntuforums.org/member.php?u=1239139")-- It could possibly be a dust issue. Since it is an older laptop there is a real good chance that there is dust trapped inside. We need to explore all possible problems before we jump to conclusions.

---

### Post by tmnuwan12 on 2011-02-09
> **Caboose885 said:**
> How long does the computer stay on before it overheats? (on average)

I would try just updating the BIOS (and no you can't run BIOS updates via wine)

If you can boot into Windows and apply the BIOS upgrade.

If you don't have Windows there are DOS methods and others that are a bit trickier.

[How to Flash BIOS]("http://ubuntuforums.org/showthread.php?t=318789")


[aloya82]("http://ubuntuforums.org/member.php?u=1239139")-- It could possibly be a dust issue. Since it is an older laptop there is a real good chance that there is dust trapped inside. We need to explore all possible problems before we jump to conclusions.

Yes, That would be my last resort. But the frequency scaling seem to work for me and I am running considerable amount of threads and temp is not hitting beyond 90C which is good. I am not sure how windows handle this because I use windows on the same machine and I never faced a situation like that. But I think if someone can implement fix for generic Linux kernel that would be great....Thanks all for your ideas guys..It is great..

---

### Post by P4man on 2011-02-09
> **tmnuwan12 said:**
> Yes, That would be my last resort. But the frequency scaling seem to work for me and I am running considerable amount of threads and temp is not hitting beyond 90C which is good. I am not sure how windows handle this because I use windows on the same machine and I never faced a situation like that. But I think if someone can implement fix for generic Linux kernel that would be great....Thanks all for your ideas guys..It is great..

Does your fan speed up as the cpu gets hotter? I still think its a pretty straightforward BIOS APCI issue that likely can be solved by booting one of the acpi_osi parameters explained in the link in my signature. Im guessing your cpu fan isnt increasing its speed and thats the real difference with windows.

BTW, 90C isnt good. Its terrible.

---

### Post by tmnuwan12 on 2011-02-09
> **P4man said:**
> Does your fan speed up as the cpu gets hotter? I still think its a pretty straightforward BIOS APCI issue that likely can be solved by booting one of the acpi_osi parameters explained in the link in my signature. Im guessing your cpu fan isnt increasing its speed and thats the real difference with windows.

BTW, 90C isnt good. Its terrible.

Yes, I know 90C is not good but it is ok until I find a permanent solution. 
For your information, the speed of the fan is changing. So I bit stuck to figure out what is causing this peak temperature. Now with frequency being cut down to 800MHz on both cores temp is hovering around 75C.
I not sure what exactly causing it. I also checked processes running in kernel and there are no heavy weight tasks in the background either...
Any ideas welcome..
Thanks in advance....

---

### Post by P4man on 2011-02-09
I suppose you didnt click the link I gave you yet.. "[I]acpi_osi=
This option frequently solves problems with LCD backlight, fan control problems and **misreporting of thermal events.**[/I]". I cant promise it will work, but its possible those reported temps are incorrect and its definitely worth a shot.

---

### Post by tmnuwan12 on 2011-02-09
> **P4man said:**
> I suppose you didnt click the link I gave you yet.. "[I]acpi_osi=
This option frequently solves problems with LCD backlight, fan control problems and **misreporting of thermal events.**[/I]". I cant promise it will work, but its possible those reported temps are incorrect and its definitely worth a shot.


Yes I tried that and I think it fixed it. Thanks a lot..It is something wrong with sending wrong information to BIOS..Thanks a lot guys..
Cheers.

---

### Post by psusi on 2011-02-09
> **tmnuwan12 said:**
> Yes I tried that and I think it fixed it. Thanks a lot..It is something wrong with sending wrong information to BIOS..Thanks a lot guys..
Cheers.

Yay, yet another bios that intentionally malfunctions when it detects you are running Linux.

---

### Post by P4man on 2011-02-10
> **tmnuwan12 said:**
> Yes I tried that and I think it fixed it. Thanks a lot..It is something wrong with sending wrong information to BIOS..Thanks a lot guys..
Cheers.

If you still think you fixed it, care to tell us which kernel parameter did the trick, and what the effect is on temps/fan behavior?

---

### Post by tmnuwan12 on 2011-02-10
> **P4man said:**
> If you still think you fixed it, care to tell us which kernel parameter did the trick, and what the effect is on temps/fan behavior?

But when I restart it is going back to default settings, I think I need some time to figure out what is actually going on. I will let you guys know as soon as I can..Fingers crossed..

---

### Post by P4man on 2011-02-10
Read my link carefully. If you are adding kernel options in grub, it only applies to a single boot. I explain in detail how to make those changes permanent. 

You can lead a horse to water, but you cant make it drink... ;)

---

### Post by reetawwsum on 2013-04-21
[COLOR=#333333][FONT=Arial]You could try to open the terminal, then $sudo gedit /etc/default/grub and in the line that says:[/FONT][/COLOR]
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/INDENT][COLOR=#333333][FONT=Arial]change it for:[/FONT][/COLOR]
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="**acpi_osi=Linux** quiet splash"
[/INDENT][COLOR=#333333][FONT=Arial]then save and restart. I hope this solve the problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]and [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]install bumblebee[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][http://www.ubuntugeek.com/install-bumblebee-in-ubuntu-12-1012-04-using-ppa.html](http://www.ubuntugeek.com/install-bumblebee-in-ubuntu-12-1012-04-using-ppa.html)[/FONT][/COLOR]

---

### Post by Elfy on 2013-04-21
They might have 2 years ago.

Closed

---

