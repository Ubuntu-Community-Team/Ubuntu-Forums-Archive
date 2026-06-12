---
title: "Hoary  boot log"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by mtron on 2005-04-13
I have a small bug on my system, but i really can't figure it out. The reason: hoary boots up  to fast.   :grin: 

I installed splasy and it goes back to the verbose output due to an error, but as soon as I am back in the usual boot output gdm starts, so i get a black screen and some seconds later the login screen. 

I can't see a (failiure) message, when I boot without the splash, but when I changed from warty to hoary I realized that ubuntu also uses a "trick" to start gdm and then loads some other services, before the login screen comes up. 

Where can I find a log of the boot process that might give me an information? The last thing I can see is that .ICEAuthority is ok, so what services are loaded after that?


Thanks!

---

### Post by haaglin on 2005-04-13
It is probably this error: 

"t_kernel_font: Invalid Argument"

Dont know how to fix it though, but i get this problem on 3 computers when using splashy, an have seen others get it too. You can turn off the "go to verbose when an error occured" thingy in /etc/splashy/config.xml

---

### Post by mtron on 2005-04-13
a small workaround for the splashy error issue: 

$ sudo gedit /etc/splashy/config.xml

set <errorimg>/etc/splashy/background.jpg</errorimg> and 
      <autoverboseonerror>no</autoverboseonerror>

Thanks haaglin!

but where can I find a log about the boot process please?

---

### Post by Goshawk on 2005-04-13
Yes 
 <autoverboseonerror>no</autoverboseonerror>
this is one of the best features of splashy

mtron: really there is nothing that logs all messages in the screen (maybe splashy can do it in futer version). To see your error you have to press F2 at the beginning of boot time (it will diable splashy) and you can figure out the error if you read the console..

thanks for your support

---

### Post by mtron on 2005-04-13
Hi! 

Like I said, when I boot using F2  I can't see a failiure message. Anyway I would have noticed it before. 

I came across this failiure only because splashy (thanks again for this nice software) showed the error screen... 

I think the reason that i never saw a boot pu failiure message is that gdm sarts, and during the gdm starting process ( where you see a black screen) some services are loaded in the background . e.g. Apache does it like this. 

But anyway, i will make some more research.

---

### Post by haaglin on 2005-04-13
The error isn't displayed if you go to verbose mode in the early stage of splashy. It is the same as for me. Only if i let the splashy continue, you will get this error.

---

### Post by nad on 2005-04-13
There are literally dozens of log files created by systems and applications in linux. View the contents of your /var/log directory for some of them. Your current session log is easily accessed by the command ' dmesg ' (from your current boot forward). Pipe it through more or less for one screen full of information at a time. Or ' tail /var/log/messages ' for the last ten lines added to the current session log.

Some of the logs you may want to review are /var/log/Xorg.0.log and /var/log/gdm/:0.log. These are your most recent logs dealing with gdm and the X server. Older logs are available.

Dan M

---

### Post by Goshawk on 2005-04-13
nad.. yes it shoudl be useful but not for this program.
Splashy reads from /dev/vcs1 and if it reads: [fail], error, command not found it goes to verbose mode. If you get this error when the system is half booted and you wanna see what's wrong, afther booting process do:
CTRL + ALT + F1, you will be redirectf in the tty1 where boot messages are: read there is you get the words that causes an error for Splashy.

---

### Post by nad on 2005-04-13
Hmmmm...

I'm going to have to check this out. Thanks for the lead.

Dan M

---

### Post by mtron on 2005-04-14
Great. Now I found my error. Like haaglin said for me it is also 

"t_kernel_font: Invalid Argument"

I could not find anything in the debian bugs and mailinglists...

Does sb. know something about this bug?

EDIT: this problem seems to happen with more splash utilities (which require a kernel patch) the workaround is always an other kernel patch OR setting verbose to no

---

### Post by Goshawk on 2005-04-14
We are working to solve that but it seems related with framebuffer activation instead of Splashy itself

use the <noautoverbose> option for now

---

