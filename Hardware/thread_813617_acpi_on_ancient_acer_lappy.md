---
title: "acpi on ancient acer lappy"
date: 2008-05-31
forum: Hardware
---

### Post by brettg on 2008-05-31
Hi all

Have an old acer 602TER laptop (PIII650, 256Mb) which I'm using as a proxy server for my home network. It works fine but is very slow.

For quite a while I just accepted that it was slow because it is so old and i've been too busy to worry about it too much.

Now, I have a bit of free time and was going about updating to kernel 2.6.24.17 whatever and was poking around while waiting for the download to complete.

What I noticed was that a process "kacpid" is eating between 85 and 97% of my cpu cycles constantly. 

So, I do some googling and see many suggestions regarding adding the acpi=off kernel parameter. Sounds reasonable, thinks I, the lappy is pre 2000 so the acpi implementation is going to be rubbish and I probably should have thought of that myself. 

So I added acpi=off and did a reboot . . . . KERNEL PANIC

More googling, and a few people also suggest noacpi as well as accpi=off, so I add that and again . . . . . KERNEL PANIC

So, remove both paramaters, reboot, everything is fine, 'cept kacpid is still chewing cycles.

More googling, found a few lucky chaps who have the same model laptop who've done the very same thing and it worked for them. Must have different BIOS version is all I can think of.

So back to google looking for BIOS updates but can't find any. Acer only support back as far as the Travelmate 620 (like it would hurt them to host legacy files on their server . . . grrrr)

So now I've turned to here.  

If anybody has any suggestion as to how I can kill the kacpid process (and no, I can't kill -9 it, I tried) then I would very much appreciate the advice.

The machine is working fine but I HATE when I know something on my network is broken and I can't fix it. I feel like somebody's gonna knock on my door and confiscate my geek card. 

Or something.

---

### Post by Rocket2DMn on 2008-05-31
Try installing bootup manager
```
sudo apt-get install bum
```
Then from System->Administration->Boot-up Manager  (or if you are in Kubuntu, whatever the equivalent is).  You should be able to disable acpid related processes from here. There is also the more basic System->Administration->Services

---

### Post by brettg on 2008-06-01
Thanks for the reply Rocket2DMan

I probably should have mentioned that (due to the low specs of the acer) I'm running 8.04 server without a gui, so any solution needs to involve command line hacking. Having said that you have given me a clue. I might google around and learn more about controlling services from the cli.

Just as an aside, I notice during boot that there are some acpi services loading that are specifically prefixed with acer, eg, Loading acer_apci or similar. Maybe if I can stop those from loading then I can turn off acpi and fix the problem that way.

Thanks again.

---

### Post by Rocket2DMn on 2008-06-01
You can always stop a service with
```
sudo /etc/init.d/<service_name> stop
```
I think the command you want then is
```
sudo update-rc.d -f <service_name> remove
```
Then you can reboot and it should be stopped from autoloading.  I'm not sure if other dependencies are needed before you run that command, see what happens.  You can always check man pages, too.

---

### Post by brettg on 2008-06-26
The latest kernel update (2.6.24-19) solved the problem of the kacpi daemon thrashing so all is well. Thanks all for the help.

---

### Post by brettg on 2008-07-02
Nope, everything was OK for a couple of days and then wham, back to the old problem. Rebooting doesn't seem to make a difference either. WTF?

---

### Post by Rocket2DMn on 2008-07-02
Try booting with the kernel option
```
acpi=off
```

---

### Post by brettg on 2008-07-02
Thanks Rocket2DMan

I've tried that, along with apm=off alcp=off and some other stuff I can't remember. For some reason this particular laptop throws a kernel panic if you use acpi=off. grrrr. 

It's a kernel bug that affects post 2.6.18 kernels.

So, I am currently downloading 6.04LTS server so that I can use an older kernel 

<sigh>

---

