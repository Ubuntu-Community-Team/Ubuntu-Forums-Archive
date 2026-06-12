---
title: "Memory speed incorrect / flash video problems"
date: 2011-05-31
forum: Hardware
---

### Post by no_numb on 2011-05-31
I'm running ubuntu natty on my acer aspire one 521 netbook. I upgraded the ram to 4gb 1066 ddr3 from 1gb 1066 ddr3.

I ran lshw in the terminal and got this back for the memory:

 ```
*-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             vendor: Micron Technology
             physical id: 0
             serial: 00000000
             slot: S1
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
```


Clock of 667MHz?

Now because its a netbook it has nothing useful in the bios for adjusting settings (running 1.08). Used to be a dual boot win 7 starter and ubuntu but I installed a ssd so cant check in windows. Any suggestions?

Another thing is flash video is terrible! Really stutters playing even 360p video and sometimes the flash player thing doesnt even come up just a blank space where the video/controlls should be. Its an amd netbook with an ati 4225 graphics card, catalyst is installed. Played ok in windows but as I said before I no longer have windows on the netbook.

---

### Post by no_numb on 2011-06-01
Bump :)

---

### Post by gordintoronto on 2011-06-01
I went looking for DDR3 memory, and the slowest I could find was 1066. However, that doesn't mean that it will run at that speed in your motherboard. Did you look at the memory speed in lshw before removing the old memory? If the memory could run faster, I think there would be a setting in the BIOS.

You computer's CPU is grossly slow, so I am not surprised that it struggles with flash.

---

### Post by no_numb on 2011-06-01
I have not tested the ddr3 which came with it perhaps I'll stick it back in and run a test. The bios is very very limited pretty much only boot order can be changed.

The cpu/graphics card does alright in windows though.

see here [http://www.youtube.com/watch?v=f0q0aWfVdN8&feature=related](http://www.youtube.com/watch?v=f0q0aWfVdN8&feature=related) playing youtube HD

The processor is about the same speed as the n450 according to a lot of websites.

---

