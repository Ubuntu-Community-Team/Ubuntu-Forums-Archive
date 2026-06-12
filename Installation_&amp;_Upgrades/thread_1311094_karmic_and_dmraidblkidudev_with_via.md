---
title: "karmic and dmraid/blkid/udev with via"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by jasmine55 on 2009-11-02
hi,
this weekend I installed karmic on a via raid1 array (vt8237).
It is using dmraid to recognize the array.

But during the boot process the system hangs, it can not discover the mountpoint for the rootfs (/dev/mapper/via_xxxxxy).
In the initramfs console I have to activate the raid array with "dmraid -a y" then it works.

I examined the situation and discovered, that udev with blkid is responsible for calling "dmraid-activate sdX" using the udev rule in /lib/udev/rules.d/85-dmraid.rules

SUBSYSTEM=="block", ACTION=="add|change", ENV{ID_TYPE}=="disk", ENV{ID_FS_USAGE}=="raid", KERNEL=="hd[a-z]|sd[a-z]", \
        RUN+="/sbin/dmraid-activate %k"

udev gets "ID_FS_USAGE" from blkid. If I call blkid directly on the device (blkid -p /dev/sdd), there is no outpu. So the reason for the problem is, that blkid does not see, that this block device is being used for a raid array.

So I downloaded the source of the util-linux package, which contains the source of blkid. Within this package there is the file shlibs/blkid/src/probers/via_raid.c

In this file, you can find that:
```


struct via_metadata {
        uint16_t        signature;
        uint8_t         version_number;
        struct via_array {
                uint16_t        disk_bit_mask;
                uint8_t         disk_array_ex;
                uint32_t        capacity_low;
                uint32_t        capacity_high;
                uint32_t        serial_checksum;
        } array;
        uint32_t        serial_checksum[8];
        uint8_t         checksum;
};

........
 if (!via_checksum(v))
                return -1;
........

/* 8 bit checksum on first 50 bytes of metadata. */
static uint8_t via_checksum(struct via_metadata *v)
{
        uint8_t i = 50, cs = 0;

        while (i--)
                cs += ((uint8_t*) v)[i];

        return cs == v->checksum;
}


```The problem seems to be, that the checksum-check doesn't work.

If I extract the raid-metadata with dmraid, it looks like this:

```

00000000   55 AA 00 0C  04 40 AF F1  49 17 00 00  00 00 F5 D6  U....@..I.......
00000010   90 D2 F2 C2  7A CD F5 D6  90 D2 00 00  00 00 00 00  ....z...........
00000020   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00000030   00 00 A4                                            ...

```So the checksum is "A4". If I printf the variable "cs" I get as result "A4" - so the checksum calculation works well.
But if I printf the variable "v->checksum" I get "00". What is the reason for that?

So I also printed the addresses of the variables in the via_metadata structure instance "v":
```

 printf("Variable memory addresses: structure base: %p, signature: %p, version_number: %p, array: %p, serial_checksum: %p, checksum: %p\n",v,&v->signature,&v->version_number,&v->array,v->serial_checksum,&v->checksum);

Variable memory addresses: structure base: 0xe55310, signature: 0xe55310, version_number: 0xe55312, array: 0xe55314, serial_checksum: 0xe55324, checksum: 0xe55344

```As you can see, the checksum uint8_t is at the wrong address. According to the structure base, which is at 0xe55310, the checksum is at 0xe55310+dec2hex(50)=  0xe55342 but the checksum variable is pointing to 0xe55344.

If I look at the printf output (memory addresses) the variable "array" is 2 bytes next to "version_number" despite the fact, that version_number is of type uint8_t but seems to consume 2 bytes of memory instead of 1 byte. This also happens with disk_array_ex, so we have for the checksum 2 bytes difference from the real address.

So why needs uint8_t 2 bytes of memory???

If I change the code like this:
  return cs == v->checksum;
=>  return cs == ((uint8_t*) v)[50];

In this case, the correct memory address for the checksum comparison is used and blkid recognizes the array successfully:
/dev/sdd: VERSION="0" TYPE="via_raid_member" USAGE="raid"

Now, if I build the deb package with this change, and run blkid from /sbin/blkid instead of running it from the package source directory, it does not recognize the drive again....???

Another thing:
I found out, that there is another script in the initramfs which uses dmraid to discover the raid arrays. dmraid is discovering the array successfully, but dmraid-activate is being called with wrong parameters:

```

# Activate any dmraid arrays that were not identified by udev and vol_id.

if devices=$(dmraid -r -c); then
        for dev in $devices; do
                dmraid-activate $dev
        done
fi

```"dmraid -r -c" outputs :
/dev/sdd
/dev/sdc

According to this, dmraid-activate is being called with "/dev/sdd" and "/dev/sdc" as parameters. But according to the source of dmraid-activate it needs to be called with "sdd" and "sdc" (without "/dev/").
This needs to be corrected to get a working script.

It would be really great, if someone has an idea regarding the uint8_t memory usage :)
Jasmine

---

