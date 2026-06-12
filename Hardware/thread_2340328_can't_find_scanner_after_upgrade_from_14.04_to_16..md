---
title: "can't find scanner after upgrade from 14.04 to 16.04"
date: 2016-10-17
forum: Hardware
---

### Post by unclesam-xu on 2016-10-17
Hi Everyone,

I upgraded from 14.04 to 16.04. I have a samsung scx-3405FW all in one which used to work perfectly . I connect it through my router because I also have another computer for my daughter which still using 14.04. 

After upgraded to 16.04, my xsane can't find scanner anymore while my the other computer which runs ubuntu 14.04 still can find and scan from it. I reinstalled driver from samsung and still not working. printer works, just not scanner.

So my workaround now is install a windows 10 VM in virtualbox, and then install samsung windows driver and software and I can scan the network scanner from there . This showed that it is funny. the shell environment ubuntu 16.04 is not working with the scanner but the windows virtual machine within it works. a bit sarcastic.   

Is there anyone can help with this ?

thanks

sam

---

### Post by unclesam-xu on 2016-10-19
pump. no one knows?

---

### Post by col48 on 2016-10-19
Others are likely to have more useful contributions, but....


Is the driver up to date?
Is it the same one as you had in 14.04?
Have you tried looking for a different scanner app?

The reason for the last question is that xsane does not drive my Canon mfp [although I have not tried this since switching to 16.04], whereas specialist software from outside the Canonical repositories works fine.

---

### Post by alexeyn on 2016-10-19
run ls /dev 
just to start.

also try 
rm  ~/.gimp/pluginrc
and  'gimp' after

and [http://tldp.org/HOWTO/Scanner-HOWTO/dev-intro.html](http://tldp.org/HOWTO/Scanner-HOWTO/dev-intro.html)

---

### Post by gifford on 2016-10-19
Check in usr/local/samsung/sane and see if your ip address for the printer/scanner is correct.

---

### Post by unclesam-xu on 2016-10-20
here is ls:

```
sam@sam-System-Product-Name:~$ ls /dev
autofs           lightnvm            ram4      tty21  tty54      ttyS28
block            log                 ram5      tty22  tty55      ttyS29
bsg              loop0               ram6      tty23  tty56      ttyS3
btrfs-control    loop1               ram7      tty24  tty57      ttyS30
bus              loop2               ram8      tty25  tty58      ttyS31
char             loop3               ram9      tty26  tty59      ttyS4
console          loop4               random    tty27  tty6       ttyS5
core             loop5               rfkill    tty28  tty60      ttyS6
cpu              loop6               rtc       tty29  tty61      ttyS7
cpu_dma_latency  loop7               rtc0      tty3   tty62      ttyS8
cuse             loop-control        sda       tty30  tty63      ttyS9
disk             mapper              sda1      tty31  tty7       uhid
dri              mcelog              sda2      tty32  tty8       uinput
drm_dp_aux0      mei0                sda5      tty33  tty9       urandom
drm_dp_aux1      mem                 sg0       tty34  ttyprintk  usb
ecryptfs         memory_bandwidth    shm       tty35  ttyS0      userio
fb0              mqueue              snapshot  tty36  ttyS1      vcs
fd               net                 snd       tty37  ttyS10     vcs1
full             network_latency     stderr    tty38  ttyS11     vcs2
fuse             network_throughput  stdin     tty39  ttyS12     vcs3
hidraw0          null                stdout    tty4   ttyS13     vcs4
hpet             port                tty       tty40  ttyS14     vcs5
hugepages        ppp                 tty0      tty41  ttyS15     vcs6
hwrng            psaux               tty1      tty42  ttyS16     vcsa
i2c-0            ptmx                tty10     tty43  ttyS17     vcsa1
i2c-1            pts                 tty11     tty44  ttyS18     vcsa2
i2c-2            ram0                tty12     tty45  ttyS19     vcsa3
i2c-3            ram1                tty13     tty46  ttyS2      vcsa4
i2c-4            ram10               tty14     tty47  ttyS20     vcsa5
i2c-5            ram11               tty15     tty48  ttyS21     vcsa6
i2c-6            ram12               tty16     tty49  ttyS22     vfio
i2c-7            ram13               tty17     tty5   ttyS23     vga_arbiter
initctl          ram14               tty18     tty50  ttyS24     vhci
input            ram15               tty19     tty51  ttyS25     vhost-net
kmsg             ram2                tty2      tty52  ttyS26     zero
kvm              ram3                tty20     tty53  ttyS27
sam@sam-System-Product-Name:~$ ^C
```

anything I need to do next?

driver up to date.
yes, same one.
I have tried two to three app.

> **gifford said:**
> Check in usr/local/samsung/sane and see if your ip address for the printer/scanner is correct.
the ip adress is correct.

---

### Post by unclesam-xu on 2016-10-20
Ok I used a usb cable connect my computer with my scx 3405FW, the printer and scanner both work. at the same time , the scx 3405FW also connect with network but the network scan feature won't work. the other computer with 14.04 only connect through Ethernet because it is too far , but scanner work with it no problem.

---

### Post by jeremy31 on 2016-10-20
unclesam-xu
Please just edit the previous post to add new info if nobody has responded yet and use code tags- see link in my signature for terminal commands and output as it preserves formatting

Thanks

---

