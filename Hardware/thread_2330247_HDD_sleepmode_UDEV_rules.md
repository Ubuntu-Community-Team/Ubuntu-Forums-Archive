---
title: "HDD sleepmode UDEV rules"
date: 2016-07-09
forum: Hardware
---

### Post by S.User on 2016-07-09
Hi all,

I wanted to put my 3 HDDs to sleep when not needed.
The machine acts like a server so it's on all day. Hence some sound and power management is a good idea.

However, only one HDD goes to sleep, two stay alove.

So here's some output as an overview:

```
sudo blkid
/dev/sda1: UUID="[COLOR=#0000ff]f6bd81f4-418f-4d73-8acc-e23445e84887[/COLOR]" TYPE="ext4" 
/dev/sda2: UUID="ba1df120-1d5a-4eb0-b466-1833b1f97d89" TYPE="ext4" 
/dev/sda3: UUID="f0456fac-dc73-4fdf-97ea-70ac926b0786" TYPE="swap" 
/dev/sda4: UUID="05aa9340-3cdd-41ef-ac4b-519f356b7e61" TYPE="ext4" 
/dev/sdc1: LABEL="GB160A" UUID="[COLOR=#0000ff]9ec31ffa-1a99-4a1d-9caa-355316d375f1[/COLOR]" TYPE="ext4" 
/dev/sdb1: LABEL="GB160" UUID="[COLOR=#0000ff]4aca62bc-38e1-41d8-b866-c3e38b420bbc[/COLOR]" TYPE="ext4" 

```
```

sudo hdparm -C /dev/sdb
/dev/sdb:
drive state is:  standby

sudo hdparm -C /dev/sdc
/dev/sdc:
drive state is:  active/idle

sudo hdparm -C /dev/sda
/dev/sda:
drive state is:  active/idle

```


The UDEV rule looks like this:

```
SUBSYSTEMS=="scsi", KERNEL=="sd?1", ATTRS{model}=="WDC WD400BB-75DEA0", RUN+="/sbin/hdparm -S 120 
/dev/disk/by-uuid/[COLOR=#0000ff]f6bd81f4-418f-4d73-8acc-e23445e84887[/COLOR]" 
SUBSYSTEMS=="scsi", KERNEL=="sdb1", ATTRS{model}=="ST3160215ACE", RUN+="/sbin/hdparm -S 120 /dev/disk/by-uuid/[COLOR=#0000ff]4aca62bc-38e1-41d8-b866-c3e38b420bbc[/COLOR]"
SUBSYSTEMS=="scsi", KERNEL=="sdc1", ATTRS{model}=="WDC WD1600AAJS-08B4A0", RUN+="/sbin/hdparm -S 120
/dev/disk/by-uuid/[COLOR=#0000ff]9ec31ffa-1a99-4a1d-9caa-355316d375f1[/COLOR]"

```

So sdb1 goes on standby after 2 minutes, the others don't
Sdc1 is similar to sdb.
Sda is labelled sd?1, not sure if this is right. I was trying to get all subpartitions of this HDD into one rule. I also tried calling it sda? with no different result.

What could be wrong here?
Have I missed something in the UDEV rule?

St

---

### Post by DuckHook on 2016-07-10
I assume sda is used for /. The hdd used for / will always remain active and cannot be put to sleep using hdparm. If sdc is used for any system files, it will behave likewise. e.g. swap, /tmp, etc. Also, some hdds esp older ones will not standby or sleep.

For your purposes, you may be better off activating automatic suspend and defining a proper inactivity period.

---

### Post by DuckHook on 2016-07-10
I am also wondering why you chose the UDEV route. hdparm already comes with a config file that can be modified to do what you want:```
sudo nano /etc/hdparm.conf
```Add following stanza at end for each hdd you want to activate standby, changing device ids as appropriate and timings to your needs (this is mine from my homebuilt NAS):```
# Added by duckhook 2014-06-11 to invoke standby on sdb
/dev/disk/by-id/ata-Hitachi_HDS721010CLA332_JP6930HD2DM3LF {
	apm = 127
	keep_features_on_over_reset = on
	spindown_time = 240
}

```*NOTE* apm value must be 127 or less. Any higher apm value will prevent hdd from spinning down ever.

The hdparm.conf file is unusually well commented and lists most of the useful parameters that can be invoked. Though both methods work, it is good practice to use the tools already provided when trying to invoke services because there is more documentation and support.

*FURTHER NOTE* The hdd on which / resides still cannot be put to sleep irrespective of method used. I worked around this limitation by using a small, cheap ssd for sda that draws almost no power and makes no noise.

---

