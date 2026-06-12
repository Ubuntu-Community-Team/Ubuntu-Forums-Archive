---
title: "Restore Drive USB"
date: 2013-07-03
forum: Hardware
---

### Post by daniele89 on 2013-07-03
Hello everyone! I have a problem with a Kingston USB drive (DataTraveler G3 8GB).


Time ago I used NTFS as file system after a little happens that is not detected anymore!

By Linux I can see it only with Gparted:
     It said that space is not allocated and asked me to create the partition table,
     but when I do it (msdos) after a few seconds I get a window that says input error,
     from that moment I no longer see it (I always refer to GParted) and I have to unplug/plug 


Windows tells me if I want to format it but after a few seconds it says that it's not possible to complete the format.


Could you help me? :confused:
10q in advance

---

### Post by Mark Phelps on 2013-07-03
Sorry to say this, but I have found USB sticks to be unreliable in general.  If neither Linux nor Windows can format the stick, it is simply corrupted in hardware and useless.

---

### Post by daniele89 on 2013-07-03
> **Mark Phelps said:**
> Sorry to say this, but I have found USB sticks to be unreliable in general.  If neither Linux nor Windows can format the stick, it is simply corrupted in hardware and useless.

It's a possibility and in that case I want to know if it's true!
However it worked for long time but after some formatting and/or some unsafely unplug (maybe due to NTFS filesystem) it stopped working!

---

### Post by varunendra on 2013-07-03
> **daniele89 said:**
> ....but when I do it (msdos) after a few seconds I get a window that says **[COLOR="#FF0000"]input error[/COLOR]**

Like Mark said above, it is most likely gone. The life of flash drives is very limited in comparison to hard disk drives, and you said yourself that "it worked for a **long** time.."

An I/O error in itself is a certificate of corruption, although fixable in many cases, but when it comes from gparted while creating a partition table, there is not much hope.

If you have another exactly identical drive, you may try 'dd' as follows, which in effect will be somewhat like a "low-level format" with a better approach -
```
sudo dd **if=**[COLOR="#006400"]/dev/sdb[/COLOR] **of=**[COLOR="#FF0000"]/dev/sdc[/COLOR]
```
where [COLOR="#006400"]/dev/sdb[/COLOR] is the fresh drive and [COLOR="#FF0000"]/dev/sdc[/COLOR] is the current corrupt drive (if=input_file, of=output_file).

In case of an I/O error, it is not likely that anything would be able to fix it. But it won't hurt to try if you do have an identical drive, just make extra-sure to use the drive names correctly in the dd command, or you'll end up corrupting the fresh one too.

---

### Post by daniele89 on 2013-07-03
I don't have an identical drive so I searched to "low-level format", but no way...
I tried
```
[COLOR=#000000]*sudo dd if=/dev/zero of=/dev/sdx*[/COLOR]
```
and
```
[COLOR=#000000]*sudo dcfldd if=/dev/zero of=/dev/sdx*[/COLOR]
```
but although they both go well, nothing has changed! :(

so I believe that I have no possibility to save it! :(

thank you for the help...

---

