---
title: "VHDL for Linux (Altera MaxPlus II)"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by meistwer on 2006-01-02
Hi there...

Happy new year to everyone!!!!:D 

My quuestion is about a VHDL simulator and compiler for Linux. I know that there's a tool call ghdl which I have installed but I dont know how to start i:confused: t, (I'm a fresher in Linux) and also I think it doesn't have a GUI as I couldnt find any reference about it in what I've read so far about ghdl. I really need th GUI as I need to see the waveforms, set clock speeds, the design of the hardware to add new gates, devices and stuff like that.
Is there any emulator in Linux that would allow me to run Windows stuff like ALtera maxplus 2?

Thanks a lot guys for your help, that is the best of the linux community.


Roberto

---

### Post by [Rui] on 2006-01-02
Hi,
Open menu System->Administration->Synaptic and search for hdl
select... install...

---

### Post by RockinRob2258 on 2006-08-31
/bump
I'm a Xilinx kid though.  Basically the same question.  The impression I've gotten so far though is that ghdl is almost a program that just checks your .vhd files for errors and bad links to libraries, other files, etc.  
So, ghdl is probably good for "compiling" (I use that term loosely here) .vhd files, but you still need synthesis, optimization, and "burning" tools.
Thanks

---

### Post by wPwLUi3N on 2007-11-02
IS there an vhdl simulator available in linux?

I recently switched completely to linux .... i used orcad in windows.

Please help ... i need the simulator for my engineering studies.

Thanks.

---

### Post by aafontoura on 2007-11-08
I've used MaxPlus II for ubuntu, using wine...
it's works perfectly...

---

### Post by xylometazolin on 2007-11-28
> **anuj.pathania said:**
> IS there an vhdl simulator available in linux?

I recently switched completely to linux .... i used orcad in windows.

Please help ... i need the simulator for my engineering studies.

Thanks.

As alread mentioned above, ghdl is a good vhdl simulator. You can install it via aptitude.
To visualize to results of the simulation, I use gtkwave. I advice you to use gtkwave 3.0 or better.

When using ghdl, you can write test benches like that:
[http://ghdl.free.fr/ghdl/A-full-adder.html#A-full-adder](http://ghdl.free.fr/ghdl/A-full-adder.html#A-full-adder)

---

