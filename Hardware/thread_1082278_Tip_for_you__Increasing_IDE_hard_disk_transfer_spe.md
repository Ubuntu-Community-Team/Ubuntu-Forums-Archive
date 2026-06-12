---
title: "Tip for you : Increasing IDE hard disk transfer speeds"
date: 2009-02-27
forum: Hardware
---

### Post by nickdbliss on 2009-02-27
Well Hard disks, due to their design and inclusion of moving parts, are a major factor for bottlenecks in current desktops. Most IDE drivers support 32-bit transfers, but most distributions default to 16-bit transfers for safety and compatibility purposes. So to check whether your hard disk supports 32-bit transfers, write this in the terminal:

sudo hdparm -c3 /dev/sdX

where X may be a,b,c or d for most desktops. It is safe to try all the letters. If the above command does not give any output error like the one below then it means 32-bit transfer is supported.

HDIO_SET_32BIT failed: invalid argument

And to use it, add the command:

hdparm -c3 /dev/sdX

(where again X may be a,b,c,d as u found above) to /etc/rc.local before the "exit 0" line.
I used this after fresh installation of intrepid so thought to share with u guys. thanks.

---

### Post by dannyboy79 on 2009-02-27
I don't think it works on sata drives (if that's what you have, there's a program called sdparm that can maybe set that) as I tried it on my mine and it gave the "HDIO_SET_32BIT failed: invalid argument" as well but for all my other drives it stated this: "/dev/hdd:
 setting 32-bit IO_support flag to 3
 IO_support   =  3 (32-bit w/sync)"
the message above would lead me to believe that it actually worked at set the bit transfer rate to 32.
Also, wouldn't you think that this could lead to a hard drive dieing sooner?

---

### Post by nickdbliss on 2009-02-28
> **dannyboy79 said:**
> I don't think it works on sata drives (if that's what you have, there's a program called sdparm that can maybe set that) as I tried it on my mine and it gave the "HDIO_SET_32BIT failed: invalid argument" as well but for all my other drives it stated this: "/dev/hdd:
 setting 32-bit IO_support flag to 3
 IO_support   =  3 (32-bit w/sync)"
the message above would lead me to believe that it actually worked at set the bit transfer rate to 32.
Also, wouldn't you think that this could lead to a hard drive dieing sooner?

Yes it is for IDE hard disk usually know as ATA. So i am not sure about Sata drives.(i ll experiment with that) From the message u posted, the command worked very well with the drives. 

No it is safe enough to use it unless you face some data corruption problems(Errors in reading some files). In that case set it to default value but to be on safe side just have the backup of your imp files.

---

### Post by ScarySquirrel on 2009-02-28
I have a SATA drive.  :(

---

### Post by nickdbliss on 2009-02-28
OK to check if there is any speed gain. Issue this command before enabling 32-bit transfer mode :
hdparm -t /dev/hdX (where x is a,b,c or d)

You will get the speed in MB/sec. Now enable the 32-bit mode and rerun the command. See any difference in speed?

---

### Post by nickdbliss on 2009-02-28
> **ScarySquirrel said:**
> I have a SATA drive.  :(

SATA drives are usually optimized so this will work with PATA drives for now.

---

### Post by dannyboy79 on 2009-03-02
> **nickdbliss said:**
> Yes it is for IDE hard disk usually know as ATA. So i am not sure about Sata drives.(i ll experiment with that) From the message u posted, the command worked very well with the drives. 

No it is safe enough to use it unless you face some data corruption problems(Errors in reading some files). In that case set it to default value but to be on safe side just have the backup of your imp files.

I noticed you edited your post, before it said
```
sudo hdparm -c3 /dev/sdX
```
and I was pointing out to you that when you tried it for whatever drive and you got the return message of "HDIO_SET_32BIT failed: invalid argument", that meant that it did NOT work for that drive.

---

### Post by nickdbliss on 2009-03-02
yeah i did. In old kernels it is hdx whereas in new kernels it is sdx. Nevertheless sdx representation rules now. Actually in my old pc hdx representation worked so i was wondering if it has something to do with it. Anyways.thnx.Still experimenting with this.

---

