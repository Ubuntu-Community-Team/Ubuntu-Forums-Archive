---
title: "Laptop-mode cannot load"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by tkjacobsen on 2006-06-02
Using a HP nc4000 laptop-mode dosent load at startup, and i am not able to load it myselv:```
$ sudo laptop_mode start
disabled, not active [unchanged].

```

When checking the status, I get the following output:
```
$ sudo laptop_mode status


Mounts:
   /dev/hda1 on / type ext3 (rw,errors=remount-ro)
   proc on /proc type proc (rw)
   /sys on /sys type sysfs (rw)
   varrun on /var/run type tmpfs (rw)
   varlock on /var/lock type tmpfs (rw)
   procbususb on /proc/bus/usb type usbfs (rw)
   udev on /dev type tmpfs (rw)
   devpts on /dev/pts type devpts (rw,gid=5,mode=620)
   devshm on /dev/shm type tmpfs (rw)
   lrm on /lib/modules/2.6.15-23-686/volatile type tmpfs (rw)
   /dev/hda4 on /media/hda4 type ext3 (rw)
   binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Drive power status:

   /dev/hda:
    drive state is:  active/idle

(NOTE: drive settings affected by Laptop Mode cannot be retrieved.)

Readahead states:
   /dev/hda1: 128 kB
   /dev/hda4: 128 kB

Laptop Mode is NOT allowed to run: /var/run/laptop-mode-enabled does not exist.

/proc/sys/vm/laptop_mode:
   0

/proc/sys/vm/dirty_ratio:
   40

/proc/sys/vm/dirty_background_ratio:
   10

/proc/sys/vm/dirty_expire_centisecs:
   3000

/proc/sys/vm/dirty_writeback_centisecs:
   500

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq:
   600000

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:
   1400000

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq:
   600000

/proc/acpi/button/lid/C13B/state:
   state:      open

/proc/acpi/ac_adapter/C138/state:
   state:                   off-line

/proc/acpi/battery/C139/state:
   present:                 no

/proc/acpi/battery/C13A/state:
   present:                 yes
   capacity state:          ok
   charging state:          discharging
   present rate:            1166 mA
   remaining capacity:      2073 mAh
   present voltage:         11529 mV

```


Would really apreciate some help to get longer battery life.

---

### Post by konradsa on 2006-06-02
```

Laptop Mode is NOT allowed to run: /var/run/laptop-mode-enabled does not exist.

```

That tells you why it does not work. Try
```

sudo touch  /var/run/laptop-mode-enabled

```
and then try it again.

I don't know why this file always goes missing, got the same problem on my lappi.

---

### Post by tkjacobsen on 2006-06-02
Thanks. Worked perfectly.

---

### Post by ColorsInMyHead on 2006-06-07
I had the same problem and that fixed it but restarting it makes it stop working again.

Is there a way to make that work after restart?

---

### Post by the_maassk on 2006-06-08
[QUOTE=konradsa]```

[code]
sudo touch  /var/run/laptop-mode-enabled

```
[/QUOTE]

I had the same problem as the poster and like you suggested, I ran the above code. Laptop-mode came up fine but led me to another BIGGER trouble!

Now my laptop suspends itself the moment I disconnect it from mains power ](*,) . I definately do not want this! I was better off before I guess. I was manually adjusting my CPU governor and hdparm to optimize for battery life and that was ok.

Please tell me as to how can I revert back from the above command!

---

### Post by golfbuf on 2006-06-09
[QUOTE=the_maassk]I had the same problem as the poster and like you suggested, I ran the above code. Laptop-mode came up fine but led me to another BIGGER trouble!

Now my laptop suspends itself the moment I disconnect it from mains power ](*,) . I definately do not want this! I was better off before I guess. I was manually adjusting my CPU governor and hdparm to optimize for battery life and that was ok.

Please tell me as to how can I revert back from the above command![/QUOTE]

You can turn off laptop mode via:

sudo /etc/init.d/laptop-mode stop

Also, you should not have to "touch /var/run/laptop-mode-enabled", just change the last line of /etc/default/acpi-support to true to get it to start on boot and to be able to use 'sudo /etc/init.d/laptop-mode {start,stop}'.  But, make note of the comment why this is disabled and test it out for yourself.  Also, there are additional options for laptop-mode in /etc/laptop-mode/laptop-mode.conf, so edit this file according to your laptop and your experience.

I'm still testing here.

regards,

---

### Post by Offoffoff on 2007-08-05
Is it good to set laptop_mode? I see hda-settings cannot be reverted. Is it dangerous?

---

### Post by aldeby on 2007-09-10
error
```
Laptop Mode is NOT allowed to run: /var/run/laptop-mode-enabled does not exist.
```
occurs to me too when I run **sudo laptop_mode status**

creating the laptop-mode-enabled file with touch makes the program run, but for the current session only!

enabling **laptop-mode=true** in /etc/defaults/acpi-support does nothing!

the only workaround I found is starting laptop-mode by hand each time by doing **sudo laptop_mode start**

however since it needs **sudo** I am not able to set a button in my taskbar to activate it only by pushing the button.

this problem occurs both with fiesty and gutsy!

someone has any other idea?
thanks 

for reference: [https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/127273](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/127273)

---

### Post by aldeby on 2007-10-13
current version of Ubuntu cutsy 7.10 solves the problem.

laptop-mode-tools is working flawlessly now.

thankyou devs!

---

