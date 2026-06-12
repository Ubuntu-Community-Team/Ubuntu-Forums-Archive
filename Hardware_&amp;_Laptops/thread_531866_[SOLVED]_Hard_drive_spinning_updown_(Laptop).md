---
title: "[SOLVED] Hard drive spinning up/down (Laptop)"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by wieman01 on 2007-08-22
Hi Folks, 

I am running Kubuntu 7.04 on laptop PC. Recently I noticed that my hard drive is constantly spinning up & down (at least once a minute) causing a "click" sound, apparenly as part of Ubuntu's power management. Since spinning up & down can significantly reduce the life cycle of your HD, I want to disable this feature like I did in Dapper. 

But I don't know how to do that & where to start. I cannot remember when I did while I was on Dapper. Please note that the HD is fine and that the 'click' sound has definitely to do with the power management.

What I did is this, but to no avail:
> sudo gedit /etc/laptop-mode/laptop-mode.conf
Now set these values to '0':
> CONTROL_HD_IDLE_TIMEOUT=0
> BATT_HD_POWERMGMT=0
[COLOR="Red"]Does anybody know which file controls hard disk power management?[/COLOR]

---

### Post by wieman01 on 2007-08-23
Deleted...

---

### Post by wieman01 on 2007-08-26
_**SOLUTION:**_
Add startup script:
```
sudo gedit /etc/init.d/local_settings
```
Now add this:
```
hdparm -B 255 /dev/xxx
```
...whereas [COLOR="Red"]'xxx'[/COLOR] represents your hard drive.

Make it executable:
```
sudo chmod +x /etc/init.d/local_settings
```
Create symb-link:
```
sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings
```
Restart & the weird clicking sound should now have disappeared. Guess that's it!

---

### Post by louaym on 2007-09-07
> **wieman01 said:**
> _**SOLUTION:**_
Add startup script:
```
sudo gedit /etc/init.d/local_settings
```
Now add this:
```
hdparm -B 254 /dev/xxx
```
...whereas [COLOR="Red"]'xxx'[/COLOR] represents your hard drive.

Create symb-link:
```
sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings
```
Restart & the weird clicking sound should now have disappeared. Guess that's it!

many thanks to the tip; it worked for me too.

louay

---

### Post by GTdriver2012 on 2007-10-23
wieman a couple of questions from a linux newb, any help here would be much appreciated and probably extend the life of my hdd

Does this work in gutsy ubuntu 7.10?
if so, is this a permanent fix, or do you have to do this every time you boot, as I was using the hdparm -B 254 dev/sda command in the terminal every time after I boot and log in
and if this is a permanent fix for 7.10, which would be awesome and much kudos to you for finding this!!!
do I type each of these commands into the terminal one at a time, one after another?

thanks again for any help

---

### Post by Daelyn on 2007-10-23
Files in /etc/init.d/ are read at every boot (I think so, still a newbie), so, should be a permanent fix.

There are many of them, involving placing hdparm -B255 (or 254 depending on HDD), in different locations. 

I just rebooted after adding this string in /etc/init.d/ and I have not heard any click yet.

---

### Post by GTdriver2012 on 2007-10-23
thank you for the reply Daelyn, i'm really hoping this works

---

### Post by GTdriver2012 on 2007-10-23
Great..... I just tested it in ubuntu 7.10 and it works

thank you louaym for the tip, here is a simplified version for all us newb's out there

!!!!!!DISCLAIMER!!!!!!   I am not an expert at all, and I claim no responsibility for data loss or damage to your HDD if you are concerned about that, do not proceed, as I myself am unsure of the longterm affects this may have (although your hard drive parking every 5 seconds may shorten the life of your hdd to as little as a few months)  A few things to note as to what you are about to do by following these instructions.....  you are basically telling your hdd not to park its heads for a very long period of time (this is common in desktop computers).  It is, however,  common for laptops to park there hdd heads somewhat frequently to save power and potentially protect data and damage to your hdd if your laptop is dropped or jarred suddenly, which you probably should avoid anyway.... anyway here goes\


Go to your terminal in Application/Accessories/Terminal
copy this line from here and paste in your terminal

sudo gedit /etc/init.d/local_settings

hit enter and it will ask for a password, type in your password that you use to log into the computer when you turn it on (note no asterisks will appear, this is normal) once you have entered your password hit enter and a text editor window will pop up.  Copy this line from here and paste it in the window that just opened up.

hdparm -B254 /dev/xxx

*note*  after you paste this line you need to edit the part that reads xxx, you have a few options here, if you have a pata/eide hdd in your computer you need to replace xxx with hda, if you have a sata hdd in your laptop you need to replace xxx with sda. so your new line should read either 
hdparm -B 254 /dev/hda    or   hdparm -B 254 /dev/sda

once that has been edited to the correct line, go to "file" and select "save"  at this point it is safe to close the text editor window.

next step, in the Terminal window copy this line from here and paste it in the terminal.

sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings

hit enter and then close the Terminal. Reboot your laptop and TADA no more clicking, your laptop will only click (park its heads) after a very long period of inactivity.

---

### Post by GTdriver2012 on 2007-10-23
I have restarted about five different times now and it is working perfectly 8-)

---

### Post by wieman01 on 2007-10-23
As you guys have highlighted this is a permanent fix which will stick. I think the development team is aware of this issue and should fix the bug soon. I was hoping that Gutsy would fix it, but apparently this is still an issue.

Thanks, GTdriver2012, for posting your stuff as well. I was not aware of the fact that simple commands (with not further comments) can be confusing to newcomers. I usually try to convey my message in the simplest way possible, but apparently it does not always work out. :-)

---

### Post by GTdriver2012 on 2007-10-24
Your explanation was spot on for me, but I know how it is being a total newb (being one myself) I spent a month on here before even using a live cd to see what ubuntu was all about, asking so many questions to see just how linux works, and if it wasn't for people like you wieman, I wouldn't know the small, yet rapidly growing amount of info that I know.

This is a great example of why linux is so powerful, because of its great community :-D

---

### Post by GTdriver2012 on 2007-10-24
Hey wieman, how do you put the commands in your post in those darkened text boxes?????

---

### Post by wieman01 on 2007-10-24
> **GTdriver2012 said:**
> Hey wieman, how do you put the commands in your post in those darkened text boxes?????
You mean those?
```
Hello there!
```
Just to advanced editing and select "Wrap [CODE]...". I mean the # symbol. Do you see it? Or simply use the "Wrap [QUOTE]..." option. Up to you. :-)

---

### Post by GTdriver2012 on 2007-10-24
sweet man... Thanks again :guitar:

---

### Post by dbqp on 2007-12-16
Thank you! I noticed this problem after stumbling upon it from a Google search on another topic. I noticed I had the same issue, but didn't even know it was occurring until this time. This bug should be publicized more to ensure it is addressed before it becomes a weakness in the best Linux OS available - Ubuntu.

Even my FireFox sessions have "calmed" down (to say the least) and I didn't realize how significant this problem was and am very glad there is a current work-around...but it is not 'cured'.

Good Work!

BTW: IBM Thinkpad T30

---

### Post by ritzdank on 2007-12-27
I am running into some troubles with my SATA 100GB 7200rpm drive on ibm x61s (7.10 gutsy) and hope there is someone who can help me on that issue. I tried all various smartctl settings and suggested things posted to this thread but indeed:

[CODEsudo hdparm -B 255 /dev/sda[/CODE]

gave me as answer:

```
/dev/sda:
 setting Advanced Power Management level to disabled
```

but still, i can hear a weird clicking (approx. every sec.) from the harddisk when the computer is idle (if cpu has something to do, it never clicks, at least not noticeable). This never happens in winXP, i have to say, unfortunately. I also followed this documentation about this strange thing here: [http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking]("http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking")

After trying this particular command:

```
smartctl -o on /dev/sda  
```

stopped for a while, but now it's back again!!!

Thanks

---

### Post by dbqp on 2008-01-05
How would one go about reversing this solution?

I have a VERY slow startup now when rebooting and my VM Ware machines have experienced some strange issues.

dbqp

---

### Post by wieman01 on 2008-01-05
> **dbqp said:**
> How would one go about reversing this solution?

I have a VERY slow startup now when rebooting and my VM Ware machines have experienced some strange issues.

dbqp
Just do:
> sudo rm /etc/rc2.d/S99local_settings
That will delete the link.

---

### Post by dbqp on 2008-01-05
> Just do:
Quote:
sudo rm /etc/rc2.d/S99local_settings
That will delete the link.

So I am just removing this sym link and I do not need to change anything back within the files which were previously changed?

Thanks for such a quick reply!

---

### Post by wieman01 on 2008-01-06
> **dbqp said:**
> So I am just removing this sym link and I do not need to change anything back within the files which were previously changed?

Thanks for such a quick reply!
That is right. You could also delete the script, but that's not really necessary. Only the link activates it.

_**EDIT:**_
If you like to remove the script as well, do:
> sudo rm /etc/init.d/local_settings

---

### Post by annapitcher on 2008-03-11
Thanks wieman for the solution, I've been running my presario with new hard drive for about 2 years now .. Its a fujitsu 80gb, it was making that "click" noise whole the time once in 5 secs avarage. But sometimes every 2-3 secs. In windows it was ok. It was the same in gentoo, but I solved two OSes now thanks to you.

Poor drive it was parking his head for 2 years since purchase but it works quite well for now (knock knock ..).

have fun,
peter

---

### Post by Kiri on 2008-03-31
This fix seems to have calmed my HD down too. 
Thanks.

Note that setting HDPARM to 254 sets the power management to the lowest setting. Setting it to 255 would turn it off completely, and as you decrease the value, the level of power management gets higher (I think 180 is the default value). So if you want some power managment, you might want to try messing around with the value until you find one that is good for you.
My laptop is usually plugged in, so I'm keeping it on 254 for now

---

