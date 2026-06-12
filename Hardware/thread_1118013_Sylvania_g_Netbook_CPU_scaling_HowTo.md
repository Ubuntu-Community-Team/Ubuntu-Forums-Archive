---
title: "Sylvania g Netbook CPU scaling HowTo"
date: 2009-04-06
forum: Hardware
---

### Post by jmd9qs on 2009-04-06
I've been working pretty much nonstop to figure out how to enable cpu scaling on the Sylvania g Netbook, and **hurray** I've figured it out. In case any others have this little comp (and are having the same problem) I'll detail some of the steps I've gone through to get this to work:

1. First thing's first: get rid of that crappy gOS! I absolutely abhor this little P.O.S. version of Ubuntu, so I decided to install several different linux distro's to test which works the best (**REMEMBER**: this is the "g Netbook", not the "Meso"; I don't know if this will work on the Meso!). So far, I've tried:

--Knoppix (6.0)
--U.N.R. (Ubuntu Netbook Remix)
--Debian (Lenny)
--Moblin
--Vector Linux (5.0-6.0RC)

All had their advantages/disadvantages, but none worked as well as I had hoped on this platform. Luckily, I have found a distro that seems to work pretty well:

--Cruncbang Linux - can be found/downloaded at:   
[http://crunchbanglinux.org](http://crunchbanglinux.org)

**NOTE**:Crunchbang is basically Ubuntu 8.10 (Intrepid), but trimmed down for performance (not to mention size: my / was about 2.5 GB after install!)

On that site, if you dig around a little, you'll find info on how to install the Crunchbang ISO onto a bootable USB stick (right here: [http://www.crunchbanglinux.org/wiki/cruncheee_installation_guide](http://www.crunchbanglinux.org/wiki/cruncheee_installation_guide)). From there you'll be able to install Crunchbang onto the g Netbook (**NOTE**: you may want to do a separate partition for your /home... it certainly came in handy for me with my several installs! That way you won't lose your data after installing...).

2. Update the OS! You need to make sure (after installation) that you have the latest Ubuntu Kernel by running these commands:

```
sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
```

(**NOTE**: I know, this is kind of sloppy, but it's what I did to get this to work...)

After updating, install cpufreq like this:

```
sudo apt-get install cpufreqd cpufrequtils
```

Once that's done, were ready to get to work!

3. Download and install the e_powersaver module. 

This step confused me a little bit... it seems like the *newest* kernel already has e_powersaver enabled, but I had to grab it online anyways... Here's what you do:

A) go to your "working directory" (for me it was /home/jmd9qs)
B) get the cpufreq .tar.bz2 (I know, you're thinking, "I just installed that!"; you are right, but bear with me, we're almost done).

```
wget http://www.a110wiki.de/wiki/images/6/65/Cpufreq-2.6.25_backport.tar.bz2
```

C) unpack the archive

```
tar xfvj Cpufreq-2.6.25_backport.tar.bz2
```

D) compile

```
cd cpufreq/
make
```

E) start the module (a few steps here)

```
sudo mkdir /lib/module/`uname -r`/cpu/
sudo cp e_powersaver.ko /lib/module/`uname -r`/cpu/
sudo depmod -ae
sudo modprobe e_powersaver
echo >> e_powersaver /etc/modules
```

Now, after these steps have been completed, the new module should be enabled and start at bootup. To check and see if it is working, run:

```
cat /proc/cpuinfo | grep cpu
```

which should return something like this:

```
jmd9qs@jmd9qs-laptop:~$ cat /proc/cpuinfo | grep cpu
cpu family	: 6
cpu MHz		: 1199.952
cpuid level	: 1

```

If it returns another value for "cpu MHz", this hasn't worked and you should retry. (Run the above command after a reboot, too. It should come back as "cpu MHz 1199.952"; again, if not, retry the steps detailed above).

O.K. Now, hopefully, your cpu supports scaling! (by default, this guide enables "on-demand" scaling... I'm not sure how do do anything else yet). 

The only other issue I've found on this little netbook is this: the sound will work through the laptop's speakers, but it will not come through the headphones if they are plugged in. 

Barring this *little* problem, I am REALLY happy so far with Crunchbang's performance! Try this out, if you have a g Netbook; I think you'll be happy!

**NOTE**: The info used to work this out comes from these sites:

[https://lists.ubuntu.com/archives/ubuntu-ar/2009-January/016136.html](https://lists.ubuntu.com/archives/ubuntu-ar/2009-January/016136.html)

[http://forum.netbookuser.com/viewtopic.php?id=668](http://forum.netbookuser.com/viewtopic.php?id=668)

---

