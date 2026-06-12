---
title: "create ramdisk over bad memory address"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by dve on 2007-06-20
Hi,

Memtest shows that I have some bad memory. As I have understood there are a few options I can do.

1. give kernel the option mem=XXX where XXX is less than the memory address of the bad part

2. do a kernel-badram-patch

3. create a ramdisk (that can later accessed through /dev/ram0 etc.) over the bad section 

Option 1 is a simple but loses 20% of my memory. Option 2 gives me a hand made kernel that won't update (I am using ubuntu because of the easy updates). So I want to do the 3rd version. I found some alternative bootloaders to grub that take ramdisk option in the form

```
ramdisk=address,size
```

and I think that even grub accepts the option

```
initrd=address,size
```

So if I set "address" to be "bad_address - 1" and "size" to be "length_of_the_bad_section+2" I get error free ram and some non working ramdisks.

So the questions are: what is the correct form for the grub ramdisk option? (I may have a typo in menu.lst, debugging in progress...) How do I create an initrd image that has dummy files at the location to be placed over the bad section?

Juha

P.S. remember to think laterally, this is russian electronics :popcorn:

---

### Post by CrispyFried on 2007-06-20
> **dve said:**
> Hi,

Memtest shows that I have some bad memory. As I have understood there are a few options I can do.

3. create a ramdisk (that can later accessed through /dev/ram0 etc.) over the bad section 


are you sure you can specify the actual memory address for the ramdisk? Ive never seen that option. but if you can you dont need an actual file in there though (as far as I know), just format it and leave it be. even empty it should cover the bad ram. or to be safe just copy any file thats big enough to it via /etc/rc.local on bootup.

I have doubts that it will work as you expect.. when you format the ramdisk it will fail the format due the the bad ram. not sure what happens then.

could you try underclocking your ram - it will increase reliability and maybe give enough leeway to get the bad cells back in spec. increase the CAS (and or decrease the mem bus) etc in the bios and run memtest. if you can boost the memory voltage (many mobos allow this) do that also.

a custom patched kernel is your best bet.

---

### Post by dve on 2007-06-21
> **CrispyFried said:**
> are you sure you can specify the actual memory address for the ramdisk? 

I am thinking a kind of a detour. If I have understood correctly I can make a random sized initrd image which I can load into the memory. This will be the /dev/ram0. Then if I create more small ramdisks with ramdisk_size=1M option, they will be /dev/ram1,2,3,4,5... After the boot I mount the ramdisk 1 and free the initrd (ram0). This should give me a reserved memory area between size_of_initrd and size_of_initrd + size_of _ramdisk. And with a bit of tweaking it should be over the bad memory.

However there are a few potholes.

Is the location of the ramdisk fixed after mounting (because before it is not, I think)?
Is there a maximum size for initrd image (we are talkin about 200M+)?
Can I mount ramdisk before I free the initrd or before anything else is loaded into memory (this would cause the memory adresses be more or less ramdom, or would it)?

I think this question is become more or less an academic one. But if there is an easy solution, it would make badram patch obsolete, hence unnecessary to touch the kernel.

Juha

---

