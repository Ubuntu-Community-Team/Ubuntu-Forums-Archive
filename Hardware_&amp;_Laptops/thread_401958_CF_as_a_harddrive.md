---
title: "CF as a harddrive"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by foureight84 on 2007-04-05
so i came across this article [http://gizmodo.com/gadgets/peripherals/addonics-compactflash-adapters-replace-notebook-hard-drives-249594.php](http://gizmodo.com/gadgets/peripherals/addonics-compactflash-adapters-replace-notebook-hard-drives-249594.php)

CF as IDE, which is a good marketing technique for those who want "ssd" but do not have the money. i want to do this for my laptop for the sake of battery life. i have a latitude x1 and with the extended battery, i only get about 3.5 hours with minimal usage. i have class for about 6 hours a day, and sometimes it's a little annoying to carry the a/c charger around. 

anyways, i already gone ahead with ordering the adapter and i will test out with some cf cards lying around. i wasn't thinking about it but some of the comments on the post make a very valid point; consumer flash cards have limited number of write cycles. now, i'm not sure what the write cycles are limited to. can anyone clarify? how fast would i expect a consumer cf card to die? and how much battery life should i expect to gain (i'm thinking at most 30 minutes)?

---

### Post by jjordan on 2007-04-05
I am interested in how this works out for you.  I did a quick Google and found this page:

[http://www.psism.com/sdcfbi.htm](http://www.psism.com/sdcfbi.htm)  It lists endurance from 100,000 cycles to 2,000,000 cycles but lists it as an MTBF.  

I had the same thoughts about write cycles so my thought was to put my Kubuntu on an 8GB CF (69 Euros here in Italy) in my laptops CF slot and still use the HD for data (and of course a backup operating system) that way I should not be writing to the CF too often.  Hmmm... gues I will have to figure out what to do with /dev.


It should not be too difficult to get rough estimate of how much you will extend your battery life.  Basically you need to figure how much power your HD is using as a percentage of total and how much the CF assembly will use.  The HD is usually the third most power hungry part of a laptop after the processor and screen.


Have you tried all the standard battery saving methods?

-j

---

### Post by foureight84 on 2007-04-05
yep. always use powersave with the cpu-freqselector on battery, and my brightness is always at level 2 (close to lowest). the problem is the extended battery is already weak. i am actually getting more battery life with linux than windows.

i will find out how everything goes once my ide adapter arrives on monday. i'm gonna find some disk benchmark tool to simulate write cycles on the cf cards. see how long it will last.

---

### Post by Brendantb on 2007-04-05
Hi, 

I tried this with a 4gb compact flash card and Xubuntu. 

I found that it was no faster than a normal hard drive, and I didn't see any appreciable increase in battery life, though I didn't actually measure the running time. 

However, the card was always being written too, even with light usage, and the installation quickly failed, with grub being unable to boot up the system. This happened in a matter of days. 

Putting the card in a card reader and attaching it to a laptop, only the / partition was readable. The swap partition had failed. 

I have reformatted the card, and checked its integrity on a Mac, and it seems to be good, so I might go ahead and try the suggestion of running the os from the pcmcia slot, and using a hard drive for swap and /home. 

About the adapter card, mine was a cheap import from china, and I needed to remove a pin to make it compatible with my laptop. Check the number of pins against the pins of the hard drive you are removing.

---

### Post by msikka on 2007-04-05
I recently bought a Sony UX 280 UMPC and then exchanged it for one with the 32 GB SSD. I really see no increase in battery life - only visible advantages are no HD access noise, and slightly quicker startup. But there is still fan noise, which is more than HD noise!

Hope that helps.

---

### Post by kerry_s on 2007-04-05
I been running test install's for a cf card install, it's a little hard to cut down on the writes, most of it is logs so i delete those which helps alot. I think the best thing would be a combination of cf & hd. I've already moved on but here's my /etc/rc.local with the settings i'm using.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exec athcool on &
exec echo 1000 > /proc/sys/dev/rtc/max-user-freq &
exec sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
exec sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
exec rm -r /usr/share/doc/* &
exec rm -r /usr/share/man/* &
exec rm -r /var/log/* &

exit 0

```

---

### Post by foureight84 on 2007-04-06
hmm here is what i found on my transcend cf card spec:

• Endurance: 1,000,000 Program/Erase cycles
• Durability of Connector: 10,000 times
• MTBF: 1,000,000 hours

it's almost the same as some industrial cards

---

### Post by foureight84 on 2007-04-06
> **kerry_s said:**
> I been running test install's for a cf card install, it's a little hard to cut down on the writes, most of it is logs so i delete those which helps alot. I think the best thing would be a combination of cf & hd. I've already moved on but here's my /etc/rc.local with the settings i'm using.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exec athcool on &
exec echo 1000 > /proc/sys/dev/rtc/max-user-freq &
exec sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
exec sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
exec rm -r /usr/share/doc/* &
exec rm -r /usr/share/man/* &
exec rm -r /var/log/* &

exit 0

```

thanks for the reply

i will try your rc script when i install the cf's over the weekend. does anyone know any good disk benchmark tool i can use to test cf's performance? i would also like to run it to see if the cards will die after certain amount of write cycles.

---

### Post by kerry_s on 2007-04-06
> **foureight84 said:**
> thanks for the reply

i will try your rc script when i install the cf's over the weekend. does anyone know any good disk benchmark tool i can use to test cf's performance? i would also like to run it to see if the cards will die after certain amount of write cycles.

Just to let you know these->

exec athcool on &
exec sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
exec sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

are for my system and won't help you, athcool is for my amd cpu, and the other 2 are to pre-cache firefox, but doesn't work with ubuntu's firefox, they split there firefox in to 3 part's(/etc/firefox, /usr/lib/firefox, /usr/share/firefox) i always delete there's and just use 1 firefox in /usr/lib/firefox.

---

### Post by foureight84 on 2007-04-06
> **kerry_s said:**
> Just to let you know these->

exec athcool on &
exec sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
exec sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

are for my system and won't help you, athcool is for my amd cpu, and the other 2 are to pre-cache firefox, but doesn't work with ubuntu's firefox, they split there firefox in to 3 part's(/etc/firefox, /usr/lib/firefox, /usr/share/firefox) i always delete there's and just use 1 firefox in /usr/lib/firefox.

thanks for letting me know. i'll apply my settings accordingly.

---

