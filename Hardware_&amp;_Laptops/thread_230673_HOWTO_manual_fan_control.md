---
title: "HOWTO: manual fan control"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by kreso on 2006-08-06
There is a way to manually control your fan speed, without using lm-sensors or fancontrol program, but always, be warned as this could screw up your computer, so read on only if you're an experienced user and *KNOW* what you're doing!

I just figured this out by browsing through the /proc directory, and imagine my suprise :)

Anyway, this works on my laptop, but should probably work on any other acpi-capable laptop:

cd to /proc/acpi/fan, you should see a few folders there. On my laptop, I see 4 folders (C256,C255,C256,C257)

if you enter one of the folders and type:

```
cat state
```

you'll see whether that fan state is on or off.

I had C256 and C257 turned on which resulted in my fan running at 55% power.


Now, to change that value you have to write to these files (become root ofcourse). I'm not sure how you can write to a file from console, so I mada small C program that opened the file, wrote a number in it and closed it.

To turn one of these states to on, write "0" and tu turn it off , write "3"

play arround with it for a while, but keep an eye on your temperatures!

---

### Post by Phatfiddler on 2006-11-08
I know this is an old post, but I decided to reply anyways after searching through the forums.  In the /proc/acpi/fan folder I have two folders listed, named FAN0 and FAN1, simple enough.

using the code " cat state " reveals that both fans are off at the moment, in which they are, so this method apparently works.

I was wondering though, if you could post the code to your program so that others may use it as well, so one does not have to manually edit the files each time they want a fan on/off?  Thanks in advance.

---

### Post by am7146 on 2007-12-09
Here's a super simple bash script I wrote to set the fans on my laptop. 

```
cat /proc/acpi/fan/*/state

echo setting

echo 3 > /proc/acpi/fan/C1ED/state
echo 3 > /proc/acpi/fan/C1EE/state
echo 3 > /proc/acpi/fan/C1EF/state
echo 3 > /proc/acpi/fan/C1F0/state

echo set

cat /proc/acpi/fan/*/state

```


For the noobs, Just 
```
gedit fansoff
```
 in your home directory to edit the file. Put this code in there.  After you do that.
```
chmod +x fansoff
```
to make it executable.
Then
```
sudo fansoff
```
to run it.

Simple, no?

Andy-

---

### Post by tuggy on 2007-12-09
I get a permission denied.. even running as root :confused:

---

### Post by apexofservice on 2007-12-24
same, 
permission denied.
even as root.

---

### Post by bittercoder on 2008-05-05
I can confirm that script worked for me on my HP NW 8240 - though I was using all 0's rather then all 3's (I want my fan's on flat out).

I couldn't seem to run it sudo'd... but su'ing to root and then executing the script worked just fine.

Thanks for the tip :)

---

### Post by windtracekimo on 2008-05-08
My laptop is Fujitsu S7110
I don't have /proc/acpi/fan/* stuffs, the directory is all empty on my machine (the fan is very idle even when cpu goes up to 60C).
Hope someone can give some ideas
Many thanks

---

### Post by macroshaft on 2008-06-18
I'm hoping someone can solve this problem as it seems to have sat here for ages. Just as the other posters in this thread state when trying to write to the state file using the line

echo 0 > /proc/acpi/fan/FAN/state

results in permission denied regardless of my state (su, sudo, both etc)
running the provided script just claims to have done it but no change.

---

