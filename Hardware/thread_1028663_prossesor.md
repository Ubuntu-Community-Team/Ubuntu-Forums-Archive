---
title: "prossesor"
date: 2009-01-02
forum: Hardware
---

### Post by smurfgod on 2009-01-02
i have an amb 1ghz processor and would like to upgrade it.before i go and drop 4-600$ on a new hdd and processor i would like to know how to tell what kind fits my mthrbd without taking it apart.is there a way.and before someone ask no i dont know what kind of board i have.thanks

smurf

---

### Post by TheLions on 2009-01-02
put this in terminal:
```
sudo apt-get install sysinfo
```
then type
```
sysinfo
```

there you'll find info about your motherboard and your cpu

---

### Post by jerome1232 on 2009-01-02
Also these two should show your socket size/slot size.

```
sudo lshw -C cpu
sudo dmidecode -t processor
```

---

### Post by smurfgod on 2009-01-02
that worked but i dont know how to read it....i cant put in a screen shot or upload a pic...but i cant read it.its bascially via technologies vt8363/8365...what that means idk.can u help me???

smurf

---

### Post by jerome1232 on 2009-01-02
> **smurfgod said:**
> that worked but i dont know how to read it....i cant put in a screen shot or upload a pic...but i cant read it.its bascially via technologies vt8363/8365...what that means idk.can u help me???

smurf

Just copy the text out of a the terminal window (click and drag to select) Then go into your reply and middle click, it'll be pasted in here. wrap the whole thing in code tags like this:
[noparse]```
text here
```[/noparse] tags



---edit--- This is an example of my hardware, my processor is a socket 754, So if i wanted to get a new cpu with out changing motherboards I would look for socket 754 processors.

```
sudo lshw -C cpu
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) 64 Processor 3700+
       vendor: Advanced Micro Devices [AMD]
       physical id: 5
       bus info: cpu@0
       version: AMD Athlon(tm) 64 Processor 3700+
       [COLOR="Red"]slot: Socket 754[/COLOR]
       size: 2400MHz
       capacity: 3GHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up rep_good nopl cpufreq

```

---

### Post by smurfgod on 2009-01-02
Processor Information
	Socket Designation: Socket-A
	Type: Central Processor
	Family: K6
	Manufacturer: AMD                             
	ID: 42 06 00 00 55 00 00 00
	Signature: Family 6, Model 4, Stepping 2
	Flags:
		FPU (Floating-point unit on-chip)
		DE (Debugging extension)
		TSC (Time stamp counter)
		PAE (Physical address extension)
	Version: Athlon(tm)                      
	Voltage: 1.6 V
	External Clock: 100 MHz
	Max Speed: 1200 MHz
	Current Speed: 1000 MHz
	Status: Populated, Enabled
	Upgrade: Slot 1
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
ok????know what??

---

### Post by TheLions on 2009-01-02
> **smurfgod said:**
> Processor Information
	Socket Designation: Socket-A


here is your answer you have Socket-A mainboard

---

### Post by smurfgod on 2009-01-02
socket am2...will that work...i typed in socket a processors and that what came up..im on newegg.com and i typed it in and the socket am2 came up...idk

---

### Post by jerome1232 on 2009-01-02
> **smurfgod said:**
> Processor Information
	[COLOR="Red"]Socket Designation: Socket-A[/COLOR]
	Type: Central Processor
	Family: K6
	Manufacturer: AMD                             
	ID: 42 06 00 00 55 00 00 00
	Signature: Family 6, Model 4, Stepping 2
	Flags:
		FPU (Floating-point unit on-chip)
		DE (Debugging extension)
		TSC (Time stamp counter)
		PAE (Physical address extension)
	Version: Athlon(tm)                      
	Voltage: 1.6 V
	External Clock: 100 MHz
	Max Speed: 1200 MHz
	Current Speed: 1000 MHz
	Status: Populated, Enabled
	Upgrade: Slot 1
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
ok????know what??

Your's is a socket A (462 pins), I don't know if they really make anything for that socket anymore, socket 754 (754 pins) is the lowest I can find for sell really. I think you will need to upgrade your motherboard if you want to upgrade your processor.

So if you wanted to upgrade the motherboard AM2 or AM2+ are the current sockets for AMD right now, intel is 775 or 1377.

---

### Post by Skripka on 2009-01-02
> **smurfgod said:**
> socket am2...will that work...i typed in socket a processors and that what came up..im on newegg.com and i typed it in and the socket am2 came up...idk

No.  You need a "Socket A" CPU...Socket A is another term for a Socket 462 CPU

---

### Post by dtrot55 on 2009-01-02
You can get a good deal on a Amd 64 X2 5400 BE on New egg...easily OC's too...thats what i have and got it for like 80 bucks...leaves more room for other fun items :)

---

### Post by Skripka on 2009-01-02
> **dtrot55 said:**
> You can get a good deal on a Amd 64 X2 5400 BE on New egg...easily OC's too...thats what i have and got it for like 80 bucks...leaves more room for other fun items :)

The AMD5400 is the wrong socket type.

---

### Post by jerome1232 on 2009-01-02
Well I think the op is going to need to upgrade the motherboard to get any sort of processor upgrade. I did a little looking around, that athlon he/she has in there is better than any of the socket A cpu's I've found so far.

Which is a bummer because if you upgrade the motherboard you will most likely need to replace the ram and (obviously if your switching socket types) processor along with it.

---

### Post by smurfgod on 2009-01-02
i appreciate the help..i really do.i have the processor(1ghz),like 512 PC100 ram if u can believe that.and a 35gig hdd.an nvidia 440 with 64mgs ram and a hella good sound card..im not into gaming,just movies and music(not streaming)what would the gods of ubuntu forums suggest for an upgrade.hdd and thats it or just a full system replacement.ohhh...and a ctx monitor.not lcd.thanks

smurf(and im a guy)

---

### Post by Skripka on 2009-01-02
> **smurfgod said:**
> i appreciate the help..i really do.i have the processor(1ghz),like 512 PC100 ram if u can believe that.and a 35gig hdd.an nvidia 440 with 64mgs ram and a hella good sound card..im not into gaming,just movies and music(not streaming)what would the gods of ubuntu forums suggest for an upgrade.hdd and thats it or just a full system replacement.ohhh...and a ctx monitor.not lcd.thanks

smurf(and im a guy)


Considering what you have...you need a new CPU, and motherboard-and new RAM, and new graphics card while you're at it, and more HDD space--you're better off buying a new machine and putting *buntu on it.  If you had several parts which could still be used-and not slow down new hardware, then "upgrading" parts would be an option, but you really don't.

---

