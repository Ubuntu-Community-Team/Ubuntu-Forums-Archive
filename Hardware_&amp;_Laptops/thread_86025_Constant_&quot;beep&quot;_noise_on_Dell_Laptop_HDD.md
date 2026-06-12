---
title: "Constant &quot;beep&quot; noise on Dell Laptop: HDD's permanent activity???"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by canard on 2005-11-04
Hi everyone.
I've migrated my Dell Inspiron 9100 from Gentoo to Ubuntu  a week ago.
Everything worked fine except one annoying thing:

At the beginning i noticed that there was a quite constant HDD activity (looking at gnome's applet or the laptop hdd led). Together with this activity ther was a small "beep" noise going on as the disk was accessed. 
After some forum search i installed laptop-mode and tweaked it a bit to reduce the HDD activity. For now i can see that it's nearly the same as when i was under gentoo; no extra HDD access can be seen from the gnome applet and HDD led.
BUT the noise is still there as before!!!! 
I also tried to tweak hdparm parmaters without success.
I tried other things like noatime options in fstab again without success.
The reason why i think the noise comes from HDD is that when i was under Gentoo (and Mandriva) i could here that noise when updatedb was running ...

I hope i'm making myself clear enough so that someone could help.:D 
I've a few topics dealing with quite similar problems but they didn't worl for me

---

### Post by Teroedni on 2005-11-04
How much memory do you got.
It may be that it is little memory left and therefore Ubuntu need to use the hardrive as virtual memory.

---

### Post by canard on 2005-11-04
well i have 510Mb of Ram and as far as i can see only 150-200 MB are used and the sxap partition is totally free....

---

### Post by Teroedni on 2005-11-04
Could you go into sytem monitor and tell me the load averages you have?

---

### Post by canard on 2005-11-04
with about 10min of uptime the load averages are: 0.14 0.20 0.1 (last 1min , 5min and 15 min)

---

### Post by Teroedni on 2005-11-04
Can you see if you ar having more than one task running?

---

### Post by Teroedni on 2005-11-04
Have you got evolution installed, do you use it
If you have it installed and not using it you may remove it. Perhaps that help.
I removed mine when i discovered it used atleast 100mb of my ram

---

### Post by canard on 2005-11-04
there are 80 tasks, 1 running and 79 sleeping.
Evolution is installed, i don't use it for the moment since i haven't configure my palm stuff yet. 
Anyway it's not running and trying to remove it will remove the metapackage ubuntu-desktop.....:???:

---

### Post by Teroedni on 2005-11-04
it is not important
The metapackage is only good for upgrading
So try it and see if it works.

---

### Post by canard on 2005-11-04
I've tried it, no change....
The ram usage is still good and the noise is there......](*,)

---

### Post by Teroedni on 2005-11-04
You sure its not the fans?
Have you tried to clean your laptop, i was gogling abit and many had problems with
trohtling and dirty fans ,so if you havent you may consider clean it a little.

If its really are the hardrive it most be some programs who are being run all the time
Try to check for process. And check who is running and not. I f you see something which looks strange post it here or trie to kill it to see what happends.

---

### Post by poptones on 2005-11-04
Is it going "beep...beep...beep...beep..." like once every second or two?

---

### Post by canard on 2005-11-04
yes, something like that, small beeps like if someone was typing a message using the Morse alphabet:
"beep....beeeeeeep-beep-beeeep....beeep-beep " and so one....:rolleyes: 
The sound is not really loud. I almost don't hear it at work because of the noise coming from other computer but at  home it's driving me crazy!!!!!

Just to check i tried to clean up the fans but everything was ok.
The thing that's really bothering me is that the noise doesn't exist when i run Windows and it was not present on my Gentoo install the day before i ran Ubuntu....

I looked again to check which processes where running but everything seems OK. I tried to stop sysklog just in case but no way.....the noise is still here.:-k 
I'll try every idea you have 'cause i don't know what to check now....:smile:

---

### Post by poptones on 2005-11-04
reboot into single user mode and let it sit there a few minutes. Report back whether it still does this.

---

### Post by canard on 2005-11-14
Sorry, but i couldn't answer last week.....
I've tried the single user mode but still no change.....
I'm wondering if my HDD's not going to die soon :???: 

Anyway if you have other suggestions i can test whatever you want...

---

### Post by grinias on 2005-11-17
[QUOTE=canard]Sorry, but i couldn't answer last week.....
I've tried the single user mode but still no change.....
I'm wondering if my HDD's not going to die soon :???: 

Anyway if you have other suggestions i can test whatever you want...[/QUOTE]

See the solution of andreas_mauser in the 6th post of  

[http://www.ubuntuforums.org/showthread.php?t=21232]("http://www.ubuntuforums.org/showthread.php?t=21232") 

It works for Hoary, but it worked for me with Breezy too.

See you

---

### Post by canard on 2005-11-24
Thanks a lot!!!!!
I modified my grub conf by adding this as proposed by andreas_mauser in the post you gave...

```
root=/dev/had5 ro pci=bios idle=halt acpi_sleep=s3_bios quiet splash
```

in fact the argument acpi_sleep=s3_bios is not necessary to stop that strange noise, apparently it is usefull if you want to instal SoftwareSuspend2.
BUT as i wanted to know exactly what these options are doing i found an interesting info on a [Gentoo WIKI page ]("http://gentoo-wiki.com/HARDWARE_Dell_Latitude_X1#Misc").
in fact > 
# idle=halt is not a good solution to this problem, since it disables all less power consuming ACPI c states. It is better just to disallow the higher c states which cause the noise (C3 and C4). Using sysfs it is easy to achieve that: echo 2 > /sys/module/processor/parameters/max_cstate.
# Another solution is patching the kernel to use a lower timer interrupt (have a look at the link for more info).

Since i have no time to test these things i'm going to use the boot options for a while...:D 
I plan to test the C state thing and to recompile my kernel to see if i can find the appropriate option using the same kernel config file as I got on Gentoo. 
I 'll post here if a get better results...

---

### Post by grinias on 2005-11-28
You are right. Since a found some time to search it, i did the trick

> echo 2 > /sys/module/processor/parameters/max_cstate 

as is suggested for Breezy and everything is ok again. 3 instead of 2 in the command above, did not work for me. I hear the noise some times in WinXP, but not in Ubuntu Linux anymore. That is very good news, don't you think? :)

---

### Post by canard on 2005-11-30
Yes that's a good news!!!
I'm just wondering what is the original value you had in the file 
```
/sys/module/processor/parameters/max_cstate
```
I think mine is actually 8....

---

### Post by grinias on 2005-11-30
Yes it was 8 for me too, but acpi supports only 4, namely C1,C2,C3,C4. 

Since C3, C4 give the noise i think that 8 it's too much :)

See you...

---

