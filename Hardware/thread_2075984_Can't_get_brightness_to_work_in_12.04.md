---
title: "Can't get brightness to work in 12.04"
date: 2012-10-25
forum: Hardware
---

### Post by chief10 on 2012-10-25
I recently switched from Debian Squeeze  because i was having some compatibility issues with my new laptop and i'm enjoying using Ubuntu. It's fast and highly compatible. 

One issue i'm having however is that I can't adjust the brightness. Ubuntu recognizes the fn keys and all that however i can't even change the brightness through the brightness menu in system settings. 

Any ideas on this?

Thanks guys and girls.

---

### Post by albandy on 2012-10-25
try adding the parameters backlight=vendor acpi_osi=Linux to grub.

---

### Post by chief10 on 2012-10-25
/etc/default/grub ?

where would you like me to put it in there?

---

### Post by Twilk73 on 2012-10-25
I am having this same issue all of my FN keys are recognized except the brightness keys. As well I can not adjust the brightness manually in the settings. This is on an asus laptop.

---

### Post by albandy on 2012-10-25
> **chief10 said:**
> /etc/default/grub ?

where would you like me to put it in there?

in /etc/default/grub

search for the line that starts with GRUB_CMDLINE_LINUX_DEFAULT
and set it like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash backlight=vendor acpi_osi=Linux"

then save and do:

sudo update-grub
sudo grub-install /dev/sda

---

### Post by chief10 on 2012-10-25
> **Twilk73 said:**
> I am having this same issue all of my FN keys are recognized except the brightness keys. As well I can not adjust the brightness manually in the settings. This is on an asus laptop.

it's unusual

literally everything else was recognized immediately - hell it was better than windows clean install.. 

i'm on a vaio ultrabook

---

### Post by chief10 on 2012-10-25
> **albandy said:**
> in /etc/default/grub

search for the line that starts with GRUB_CMDLINE_LINUX_DEFAULT
and set it like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash backlight=vendor acpi_osi=Linux"

then save and do:

sudo update-grub
sudo grub-install /dev/sda

I ran this. Completed with no errors however it didn't make the brightness keys work unfortunately.

---

### Post by chief10 on 2012-10-25
any ideas?

---

### Post by Linuxisfast on 2012-10-25
Try xbacklight and set it in terminal with the command xbacklight -set % where % is the number you wish to set for brightness value.

---

### Post by Twilk73 on 2012-10-26
> **albandy said:**
> in /etc/default/grub

search for the line that starts with GRUB_CMDLINE_LINUX_DEFAULT
and set it like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash backlight=vendor acpi_osi=Linux"

then save and do:

sudo update-grub
sudo grub-install /dev/sda

edit: this did not work for me either.

---

### Post by vandorjw on 2012-10-26
[COLOR="Red"]Grub is your bootloader. I strongly recommend leaving it alone, until you learn more, considering everything is more or less working[/COLOR]
[COLOR="Red"]**grub is already installed. do not run **[/COLOR]
```

sudo grub-install /dev/sda

```

it is enough to run
```

sudo update-grub

```
to see changes

#########################
To answer your question


```

**[COLOR="Red"]sudo[/COLOR]** gedit /etc/default/grub

```

sudo -- run a program as [COLOR="DarkOrange"]root[/COLOR]
gedit -- text editing program
/etc/default/grub -- full 'path' to the location of the text-file called 'grub'

[COLOR="DarkOrange"]Root[/COLOR] is the name of the most powerful account on a Debian/Ubuntu installation. The root user account can do everything on the machine. Root is also known as supervisor and administrator. Root's home (~) folder is /root.

---

### Post by chief10 on 2012-10-26
> **vandorjw said:**
> [COLOR="Red"]Grub is your bootloader. I strongly recommend leaving it alone, until you learn more, considering everything is more or less working[/COLOR]
[COLOR="Red"]**grub is already installed. do not run **[/COLOR]
```

sudo grub-install /dev/sda

```

it is enough to run
```

sudo update-grub

```
to see changes

#########################
To answer your question


```

**[COLOR="Red"]sudo[/COLOR]** gedit /etc/default/grub

```

sudo -- run a program as [COLOR="DarkOrange"]root[/COLOR]
gedit -- text editing program
/etc/default/grub -- full 'path' to the location of the text-file called 'grub'

[COLOR="DarkOrange"]Root[/COLOR] is the name of the most powerful account on a Debian/Ubuntu installation. The root user account can do everything on the machine. Root is also known as supervisor and administrator. Root's home (~) folder is /root.

thanks for the info

i did run sudo grub-install /dev/sda - i didn't notice anything different so i don't think i screwed anything up.. hopefully..

---

### Post by Twilk73 on 2012-10-26
> **Linuxisfast said:**
> Try xbacklight and set it in terminal with the command xbacklight -set % where % is the number you wish to set for brightness value.

I tried this and it told me xbacklight was not installed and showed me how to install it. Regardless even after installing it the problem isnt solved.

---

### Post by vandorjw on 2012-10-26
Are we talking about the backlight in your keyboard or monitor/screen.

If we are talking about screen brightness please post result of

```

ls /sys/class/backlight/

```

---

### Post by Twilk73 on 2012-10-26
> **vandorjw said:**
> [COLOR="Red"]Grub is your bootloader. I strongly recommend leaving it alone, until you learn more, considering everything is more or less working[/COLOR]
[COLOR="Red"]**grub is already installed. do not run **[/COLOR]
```

sudo grub-install /dev/sda

```

it is enough to run
```

sudo update-grub

```
to see changes

#########################
To answer your question


```

**[COLOR="Red"]sudo[/COLOR]** gedit /etc/default/grub

```

sudo -- run a program as [COLOR="DarkOrange"]root[/COLOR]
gedit -- text editing program
/etc/default/grub -- full 'path' to the location of the text-file called 'grub'

[COLOR="DarkOrange"]Root[/COLOR] is the name of the most powerful account on a Debian/Ubuntu installation. The root user account can do everything on the machine. Root is also known as supervisor and administrator. Root's home (~) folder is /root.

I saved a copy of the original line i was changing so that I could fix it if needed. Thanks for the info though.

---

### Post by Twilk73 on 2012-10-26
> **vandorjw said:**
> Are we talking about the backlight in your keyboard or monitor/screen.

If we are talking about screen brightness please post result of

```

ls /sys/class/backlight/

```

Sorry we are talking about screen brightness

ls /sys/class/backlight/
acpi_video0  acpi_video1

I typed that line in terminal and thats what came up in a blue text.

---

### Post by vandorjw on 2012-10-26
Alright that makes sense

'ls' is a command to list the contents of a folder.

So, under brightness, you have 2 controllers
1. acpi_video0 
2. acpi_video1

Do you have 2 screens?

Anyways,

please report the results of
```

cat /sys/class/backlight/acpi_video0/max_brightness

```
and

```

cat /sys/class/backlight/acpi_video1/max_brightness

```

as well as

```

cat /sys/class/backlight/acpi_video0/brightness

```

**going to sleep, see this guide, GL/HF**
[https://wiki.archlinux.org/index.php/Backlight#ACPI](https://wiki.archlinux.org/index.php/Backlight#ACPI)

---

### Post by Twilk73 on 2012-10-26
I only have one monitor

results 

cat /sys/class/backlight/acpi_video0/max_brightness
10
cat /sys/class/backlight/acpi_video1/max_brightness
10
cat /sys/class/backlight/acpi_video0/brightness
9

---

### Post by vandorjw on 2012-10-26
The next step I was going to make you take was

```

sudo echo 5 > /sys/class/backlight/acpi_video0/brightness

```

to see if we can bring you down to 50% brighness.

If this works, then maybe, (if i have some time and if i remember), show you how to map this command to a key on your keyboard.

gnight

---

### Post by chief10 on 2012-10-26
> **vandorjw said:**
> Are we talking about the backlight in your keyboard or monitor/screen.

If we are talking about screen brightness please post result of

```

ls /sys/class/backlight/

```

The one i'm talking about in the OP is the screen brightness. The results are below:

acpi_video0 intel_backlight

---

### Post by vandorjw on 2012-10-26
Sorry about hijacking your thread chief, but I am working on the same problem.

I suggest to you as well to read the arch-wiki page provided above.

---

### Post by chief10 on 2012-10-26
> **vandorjw said:**
> The next step I was going to make you take was

```

sudo echo 5 > /sys/class/backlight/acpi_video0/brightness

```

to see if we can bring you down to 50% brighness.

If this works, then maybe, (if i have some time and if i remember), show you how to map this command to a key on your keyboard.

gnight

this does nothing unforunately


> **vandorjw said:**
> Sorry about hijacking your thread chief, but I am working on the same problem.

I suggest to you as well to read the arch-wiki page provided above.

nah no dramas man

---

### Post by Twilk73 on 2012-10-26
> **vandorjw said:**
> The next step I was going to make you take was

```

sudo echo 5 > /sys/class/backlight/acpi_video0/brightness

```

to see if we can bring you down to 50% brighness.

If this works, then maybe, (if i have some time and if i remember), show you how to map this command to a key on your keyboard.

gnight

sudo echo 5 > /sys/class/backlight/acpi_video0/brightness
bash: /sys/class/backlight/acpi_video0/brightness: Permission denied

Thats the results go to bed man its no big deal. Thanks for the help ill get it fixed eventually. Thanks for the help thus far.

@cheif we are both talking about screen brightness so we are on the same page

---

### Post by vandorjw on 2012-10-26
Since I am still awake anyways, can you run
@chief
```

sudo echo 5 > /sys/class/backlight/acpi_video[COLOR="Red"]1[/COLOR]/brightness

```

since you have 2 folders

---

### Post by chief10 on 2012-10-26
> **vandorjw said:**
> Since I am still awake anyways, can you run
@chief
```

sudo echo 5 > /sys/class/backlight/acpi_video[COLOR="Red"]1[/COLOR]/brightness

```

since you have 2 folders

"no such file or directory"

sorry to keep you up

---

### Post by Twilk73 on 2012-10-26
> **vandorjw said:**
> Since I am still awake anyways, can you run
@chief
```

sudo echo 5 > /sys/class/backlight/acpi_video[COLOR="Red"]1[/COLOR]/brightness

```

since you have 2 folders

sorry i should have included that I already tried that command with the same results. I figured since I had to I should try it as well lol. It gave me the same results though. 

sudo echo 5 > /sys/class/backlight/acpi_video1/brightness
bash: /sys/class/backlight/acpi_video1/brightness: Permission denied

---

### Post by vandorjw on 2012-10-26
@Twilk73
```

sudo bash -c 'echo 5 > /sys/class/backlight/acpi_video0/brightness'
sudo bash -c 'echo 5 > /sys/class/backlight/acpi_video1/brightness'

```
This will avoid the 'permission denied. If this changes your brightness, we are on the right track. If it doesn't, then the ACPI implementation on your laptop is not fully finished, and I believe I won't be able to help you any further.


@ chief
Please check your max brighness using
```

cat /sys/class/backlight/intel_backlight/max_brightness

```
if your max brighness is less than 5, then please use something less than 5 in the following 2 commands.
I suspect max_brightness is 10. So hopeuflly one of these 2 commands will cut your brightness in half.

```

sudo bash -c 'echo 5 > /sys/class/backlight/acpi_video0/brightness'
sudo bash -c 'echo 5 > /sys/class/backlight/intel_backlight/brightness'

```

The same I said to Twilk73 counts for you as well.

Good luck

---

### Post by chief10 on 2012-10-27
> **vandorjw said:**
> 

@ chief
Please check your max brighness using
```

cat /sys/class/backlight/intel_backlight/max_brightness

```
if your max brighness is less than 5, then please use something less than 5 in the following 2 commands.
I suspect max_brightness is 10. So hopeuflly one of these 2 commands will cut your brightness in half.

```

sudo bash -c 'echo 5 > /sys/class/backlight/acpi_video0/brightness'
sudo bash -c 'echo 5 > /sys/class/backlight/intel_backlight/brightness'

```



It's telling me that max brightness is "4882"

Whatever that means.

---

### Post by chief10 on 2012-11-02
no ideas anyone :)

---

