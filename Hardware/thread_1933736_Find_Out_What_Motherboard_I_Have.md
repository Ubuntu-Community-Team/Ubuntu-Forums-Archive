---
title: "Find Out What Motherboard I Have"
date: 2012-02-29
forum: Hardware
---

### Post by arsenic_creed on 2012-02-29
Hello!
I'm looking to replace my processor (I was considering this one: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1154130&CatId=7225](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1154130&CatId=7225)) but I don't know if it's compatible.
This website ([http://www.tomshardware.com/forum/284127-28-want-compatible-computer](http://www.tomshardware.com/forum/284127-28-want-compatible-computer)) tells me how to know if my motherboard is compatible with a processor but I can't remember what motherboard I have and don't know how to find the info. System info says nothing about it and CPU-Z (run through Wine) doesn't have any info for that section. 
Any one know of where I could find this info?
(I also used:
sudo dmidecode | moreas was recommended in another thread for this but there wasn't a section that said 'base board information' like that poster found.)
Thanks!
(P.s. Also, does this processor work with Ubuntu?)

---

### Post by Mark Phelps on 2012-03-01
You talking laptop or desktop?

If the former, it's unlikely you will be able to replace the processor and motherboards tend to be customized, anyway.

If it's the latter, then open the case.  You will need not only the make and model, but also the VERSION of the board.  And, you will have to check BIOS versions as well.  Newer BIOS versions tend to support newer processors, even on the same board, as long as they are pin and voltage compatible.

---

### Post by Yellow Pasque on 2012-03-01
You may be able to discern what CPU/Socket you have with cpuinfo:
```
cat /proc/cpuinfo
```

---

### Post by arsenic_creed on 2012-03-01
@Mark Phelps - Yes, desktop. I was hoping there was a way other than opening the case, my computer isn't the easiest thing to get out so I don't like to open it unless I really need to. I don't suppose that the model or model name that come up when I use the thing that Temujin suggested is what I'm looking for?   
@Temujin - I just tried that but I'm not entirely sure what I'm looking at. Can you give me an example of what it might say for socket type when I put that into the terminal? It brings up a lot of information and I'm not sure what the majority of it is so I don't know if it's there and I'm just overlooking it.  Thanks for your help!

---

### Post by plucky on 2012-03-01
From a terminal ```
sudo lshw -c system
``` should give you your Motherboard model number.

Good Luck

---

### Post by Lisiano on 2012-03-01
I had to do a regular ```
sudo lshw | less
``` to get the model, you should be looking at the very beginning 
```
lisiano-ubuntu            
    description: Desktop Computer
    product: Aspire X3300 ()
    vendor: Acer
    serial: XXXXXXXXXXXXXXXXXXXXXX
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=Acer Desktop power-on_password=disabled uuid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
  *-core
       description: Motherboard
       product: WMCP78M
       vendor: Acer
       physical id: 0
     *-firmware
          description: BIOS
          vendor: AMI
          physical id: 0
          version: P01-B3
          date: 02/16/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
```Also it is also possible to find out the socket from your current CPU by googling the model.

---

### Post by arsenic_creed on 2012-03-02
@Lisiano - Thank you, that worked perfectly!

@Everyone else - Thanks for help. 

:(
I may not be getting a new processor after all. The only one that Tiger Direct has that is the speed I want doesn't have the same type of socket. It says 'socket LGA 1155' and the ASUS website listing of my motherboard says 'socket 775', I assume this is because my computer is a couple years old?
Know of any 2.9+ GHz processors with that socket type? (Or even better, does a socket adapter thing exist [because if they don't, they should]?)

---

### Post by dandnsmith on 2012-03-02
I googled for processors, and got [this page](http://en.wikipedia.org/wiki/LGA_775) - might help, or you could try your own google search.

---

### Post by mastablasta on 2012-03-02
> **arsenic_creed said:**
> Know of any 2.9+ GHz processors with that socket type? 

wiki says:
Intel Pentium 4 (2.60 - 3.80 GHz)
Intel Celeron D (2.53 - 3.60 GHz )
Intel Pentium 4 Extreme Edition
 (3.20 - 3.73 GHz)
Intel Pentium D (2.66 - 3.60 GHz)
Pentium Extreme Edition
 (3.20 - 3.73 GHz)
Pentium Dual-Core (1.40 - 3.33 GHz)
Intel Core 2 Duo (1.60 - 3.33 GHz)
Intel Core 2 Extreme (2.66 - 3.20 GHz)
Intel Core 2 Quad (2.33 - 3.00 GHz)
Intel Xeon (1.86-3.40 GHz)
Intel Celeron (1.60 - 2.40 GHz)
 
 
Something like htis maybe:
Intel Core 2 Extreme (2.66 - 3.20 GHz)
Intel Core 2 Quad (2.33 - 3.00 GHz)

 
 
> 
(Or even better, does a socket adapter thing exist [because if they don't, they should]?)
 
they used to exist. prepare to do some search.

---

### Post by Yellow Pasque on 2012-03-02
Assuming your mobo is compatible: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116381](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116381)

---

