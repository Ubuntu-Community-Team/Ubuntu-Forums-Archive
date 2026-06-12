---
title: "GTKWave, Icarus and Xilinx ISE [Intrepid]"
date: 2009-01-26
forum: Hardware
---

### Post by physeetcosmo on 2009-01-26
For those of you who like to develop hardware on Ubuntu, you would probably like a comparable replacement for ModelSIM. Here is the answer:

Icarus, a behavioral simulator that records State outputs based on a Stimulus input. The program uses a standard .v file (for verilog, don't know if it will port in a VHDL file, but I'm sure it will) that is opened through the software after it has been developed and compiled. I use Xilinx ISE Webpack which also works on Ubuntu (you will need to register with Xilinx to download the webpack for free), to develop my Verilog. There must be stimulus modules inserted into the main .v file, which is what Icarus will use to stimulate the hardware design.

GTKWave is a graphical interface used to see the output of a digital design when stimulated.

GTKWave is on repository and can be installed using:
```
$ sudo apt-get install gtkwave
```

Icaurs needs some dependencies installed to compile properly; it is NOT on repository and must be compiled. The needed dependencies are:
-gperf
-flex
-bison
-build-essentials

If there are other dependencies that one needs, I apologize as I already have them installed and config isn't flagging them (as they are already present:)).

After the dependencies are install, enter the following lines of code, one at a time:
```
$ wget "ftp://ftp.icarus.com/pub/eda/verilog/snapshots/verilog-20081118.tar.gz"
$ tar zxvf verilog-20081118.tar.gz
$ cd verilog-20081118/
$ ./configure
$ make
$ sudo make install
```

After I get more fluent with using these apps, I will post more on using them properly! :)

NOTE: PACE in Xilinx ISE doesn't work on the eeePC due to the graphics chip installed. I haven't found a work-around as of this post date: Jan 26, 2008.

---

### Post by tommpogg on 2011-07-01
Sound interesting... where can I find Icarus?

Thank you

---

