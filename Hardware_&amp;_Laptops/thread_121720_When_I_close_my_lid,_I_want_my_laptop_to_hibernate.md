---
title: "When I close my lid, I want my laptop to hibernate"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by hevnsnt on 2006-01-25
Hello,

I would like my laptop to hibernate when I close my lid, currently it goes to the password screen.  The Hibernate under system-logout works perfectly.  I realize I need to change lid.sh, but I am not exactly sure which lines to change.

Can anyone help?

---

### Post by jsgotangco on 2006-01-25
What make/model is this? The Laptop Testing Team has data on some machines, but most of them still don't have working close lid actions (hibernate/sleep).

---

### Post by hevnsnt on 2006-01-25
It is an HP Pavilion ZE4100

It seems as though the hibernate scripts work ok.. I just want it to work when I close the lid instead of going to the login screen. :KS

---

### Post by hevnsnt on 2006-01-27
Can anyone help with this issue?

---

### Post by Botond on 2006-01-28
Edit /etc/acpi/lid.sh

my original looked like this:
```
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    ...
```

and I've changed it like this:
```
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    /etc/acpi/hibernate.sh
else
    ...
```

And it worked. But I didn't experiment yet with opening the cover again before the hybernation process has finished.

---

### Post by Skye on 2006-01-28
I have a slightly easier solution, I think.

First, create a backup of the file (so you can restore it if this doesn't work.)

```

sudo cp /etc/acpi/events/lidbtn /etc/acpi/events/lidbtn.BKUP

```

Then, edit the lidbtn button event:

```

sudo nano /etc/acpi/events/lidbtn

```

Comment out **action=/etc/acpi/lid.sh**.
Underneath that line, put in **/etc/acpi/hibernate.sh**

Save the file (ctrl+O in nano), close it (ctrl+X in nano) and restart acpi with
```

sudo /etc/init.d/acpi restart

```

Try closing the lid and see if it works.

This is slightly more elegant that Botund's version in that it doesn't edit the actual lid.sh file, it merely changes what is called when the lid event happens.  That being said, both Botund's solution and mine should work equally as well.  Good luck!

---

### Post by Botond on 2006-01-28
> That being said, both Botund's solution and mine should work equally as well.
Well, in this case only. Be aware that /etc/acpi/events/lidbtn is being called each time you either open or close the lid. So if you write anything other than "action=hibernate.sh" it will be called on lid open and close events as well.

---

### Post by Mastershredder on 2006-02-04
Just wanted to say thanks.. I've been trying to figure out how to put my thinkpad into hibernate when i close the lid and this worked perfectly!

---

### Post by 10010 on 2006-02-05
Skye:  What exactly do you mean by comment out?

Thanks!

---

### Post by Skye on 2006-02-05
The original file should look something like this:

```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh

```

By comment out, I mean to change the original file, above, so that it looks like this:

```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/lid.sh

```

After that, you can add the /usr/sbin/hibernate line so the final file looks like this:

```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/lid.sh
action=/usr/sbin/hibernate

```

One thing to be mentioned:  I'm running a modified kernel (2.6.15 based) with suspend2 patches and drivers (a howto for kernel version 2.6.12 can be found here: [http://www.ubuntuforums.org/showthread.php?t=75443](http://www.ubuntuforums.org/showthread.php?t=75443),)  so my hibernate command my differ slightly from a normal user's- (I believe the system default is **/etc/acpi/hibernate.sh**)

Try the way above first.  If that fails, replace the /usr/sbin/hibernate command with /etc/acpi/hibernate.sh.

Feel free to contact me if you need any further help.

---

### Post by sdb2028 on 2006-03-04
I found this thread which shows how to initiate hibernate. Problem: I altered my lidbtn file as recomended but when I close the lid on my laptop it goes into complete shutdown (something by the way which doesn't even happen correctly when I click shut down from the log in screen).
I am using a Toshiba M45
Any idea how to initiate hibernate without shuting down and how to get complete shut down from the log out screen?

---

### Post by 7018 on 2006-03-05
I have the same problem as this thread
[http://www.ubuntuforums.org/showthread.php?t=139856&highlight=hibernate](http://www.ubuntuforums.org/showthread.php?t=139856&highlight=hibernate)

My machine hibernates but once initiated again my keyboard does not function.  My usb mouse still works though 
:/
I have tried both suggestions listed in this thread so far.
Any ideas?
I have a hp ze4200.

---

### Post by rorowe on 2006-03-05
(noob)
I tried this on my Toshiba satellite and closing the lid only turns the monitor off. Am I missing something with the hibernate setting? (Hibernate does work from the menu, I think)

Thanks in advance,
-Robert (rorowe)

EDIT: due to the "overheating" thing on my laptop, I have acpi=off during bootup. Does that mean my edits to the lidbtn won't work since acpi is off?

---

### Post by patrickfromspain on 2006-03-05
[QUOTE=Skye]I have a slightly easier solution, I think.

First, create a backup of the file (so you can restore it if this doesn't work.)

```

sudo cp /etc/acpi/events/lidbtn /etc/acpi/events/lidbtn.BKUP

```

Then, edit the lidbtn button event:

```

sudo nano /etc/acpi/events/lidbtn

```

Comment out **action=/etc/acpi/lid.sh**.
Underneath that line, put in **/etc/acpi/hibernate.sh**

Save the file (ctrl+O in nano), close it (ctrl+X in nano) and restart acpi with
```

sudo /etc/init.d/acpi restart

```

Try closing the lid and see if it works.

This is slightly more elegant that Botund's version in that it doesn't edit the actual lid.sh file, it merely changes what is called when the lid event happens.  That being said, both Botund's solution and mine should work equally as well.  Good luck![/QUOTE]
Thanks a lot!!!

After changing lid.sh to sleep.sh when I close my notebook's lid it goes into sleep mode!!

Now everything works fine with my laptop!!

---

### Post by Abdi110 on 2006-03-25
Yay! Thanks to this thread I've finally got my power button to start hibernation, and my sleep button to start a shutdown.

---

### Post by leo_m on 2006-07-05
I just used the GUI accessible through System|Preferences|Power Management to enable suspend upon lid-closing and the suspend option appeared on the power-off menu (previously it did not appear here nor worked) and it works fine as well.

I am using the kernel provided through Synaptic Package Manager.

---

### Post by Benitez on 2007-02-08
> **Skye said:**
> I have a slightly easier solution, I think.

First, create a backup of the file (so you can restore it if this doesn't work.)

```

sudo cp /etc/acpi/events/lidbtn /etc/acpi/events/lidbtn.BKUP

```

Then, edit the lidbtn button event:

```

sudo nano /etc/acpi/events/lidbtn

```

Comment out **action=/etc/acpi/lid.sh**.
Underneath that line, put in **/etc/acpi/hibernate.sh**

Save the file (ctrl+O in nano), close it (ctrl+X in nano) and restart acpi with
```

sudo /etc/init.d/acpi restart

```

Try closing the lid and see if it works.

This is slightly more elegant that Botund's version in that it doesn't edit the actual lid.sh file, it merely changes what is called when the lid event happens.  That being said, both Botund's solution and mine should work equally as well.  Good luck!

[SIZE="3"]Holy carp! I must congratulate you for **massive epic win!!!** =D>

Had the same problem on my Dell Latitude C610 running Xubuntu Edgy. Followed it (almost) to the letter and it worked perfectly...

The reason I say almost is because I had to change the line:
```

sudo /etc/init.d/acpi restart

```

with

```

sudo /etc/init.d/acpid restart

```

Otherwise, it worked fine! 

Can someone PLEASE PLEASE post this as sticky? Seriously, I was looking for something like this for a few days now, and also I think some other people have been having problems with this too...
[/SIZE]

---

### Post by richmooremi on 2007-02-12
I found that Skye's solution works well for me until I reboot my machine (also a Lattitude c610). Then I have to restart ACPI again. Did I do something wrong?

---

### Post by scholzilla on 2007-07-05
skye's solution didn't work for me (feisty). I had to follow Benitez's edit, otherwise I got a command not found message. Any other suggestions? Thanks!

---

