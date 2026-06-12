---
title: "Infrared on IBM Thinkpad"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by sammyboy on 2006-09-08
How can I get my built in infrared to work on my IBM laptop? I cannot find anything that even remotely seems like the correct function? Thanks all!

---

### Post by ishift on 2006-11-01
i know it's kinda old, but *bump* :)

---

### Post by Sethro on 2006-11-03
Yeah I would like to know as well...

---

### Post by tedrogers on 2006-11-13
That makes four of us that have no idea how to get irda/infrared working...so I set about finding out.

First I installed a program called ircp & irda-utils from the repo's, but couldn't get this to connect to my phone (IR was active!).

I could see the IRDA port in my Device Manager, but it looks like its not active!?

A bit more googling turned up this:

```
sudo findchip -v
```

Found NSC PC87338 Controller at 0x2e, DevID=0x0b, Rev. 2
    SIR Base 0x2f8, FIR Base 0x2f8
    IRQ = 3, DMA = 3
    Enabled: no, Suspended: no
    UART compatible: yes
    Half duplex delay = 0 us

Notice it's not enabled! Hmmmm...the hunt continues.

**_EDIT:-_**

Eventually, I found a solution to this which works for me anyway using an IBM T22.  I used the following howto as a guide [http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html](http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html), but I will try and break it down for you.

1. Go to Synaptic and from the repo's install the following....ircp, irda-utils, set-serial and toshset. Some of these may already be installed.

2. Identify the type of Irda controller you have using 

```
sudo findchip -v
```

3. Go to this link on the HowTo [http://tuxmobil.org/Infrared-HOWTO/infrared-howto-s-configuration.html](http://tuxmobil.org/Infrared-HOWTO/infrared-howto-s-configuration.html) and find your type of controller in the /etc/modules.conf section. You may or may not need to disable some of these...mine was the following - a very specific one for my IBM irda, for example:

```
options nsc-ircc dongle_id=0x09	# NSC driver on a IBM Thinkpad laptop
```

4. Copy and paste the whole of this page from the above link into etc/modutils/irda-utils file using:

```
sudo gedit /modutils/irda-utils
```

This is the page you need to copy and paste:

```
# IrDA over a normal serial port, or a serial port compatible IrDA port (SIR)
alias tty-ldisc-11 irtty

# IrCOMM (for printing, PPP, Minicom etc)
alias char-major-161 ircomm-tty     # if you want IrCOMM support

# IRLAN
# But currently the IrLAN protocol is no longer maintained
# by the Linux/IrDA core team.
alias irlan0 irlan

# To be able to attach some serial dongles
# These values are hard-coded in irattach (not instance order)
alias irda-dongle-0  tekram             # Tekram IrMate IR-210B
alias irda-dongle-1  esi                # ESI JetEye
alias irda-dongle-2  actisys            # Actisys IR-220L
alias irda-dongle-3  actisys            # Actisys IR-220L+
alias irda-dongle-4  girbil             # Greenwich GIrBIL
alias irda-dongle-5  litelink           # Parallax LiteLink/ESI JetEye
alias irda-dongle-6  airport            # Adaptec Airport 1000 and 2000
alias irda-dongle-7  old_belkin         # Belkin (old) SmartBeam dongle
alias irda-dongle-8  ep7211_ir          # Cirrus Logic EP7211 Processor (ARM)
alias irda-dongle-9  mcp2120            # MCP2120 (Microchip) based
alias irda-dongle-10 act200l            # ACTiSYS Ir-200L
alias irda-dongle-11 ma600              # Mobile Action ma600

# To use the FIR driver. This applies only to the specific device!!!

#options nsc-ircc dongle_id=0x09	# NSC driver on a IBM Thinkpad laptop
#options nsc-ircc dongle_id=0x08	# HP Omnibook 6000
#alias irda0 nsc-ircc

# options smc-ircc ircc_irq= ircc_dma=
# alias irda0 smc-ircc

# options toshoboe max_baud=
# alias irda0 toshoboe

# options w83977af_ir io= io2= irq= qos_mtt_bits=
# alias irda0 w83977af_ir

# IrNET module...
alias char-major-10-187 irnet       # Official allocation of IrNET
```

For me to get this working, all I did was uncomment the option before NSC driver for IBM Thinkpad...the rest of it I left as it was. Maybe you could do the same except don't uncomment the NSC driver part. Basically though, you'll need to do some home work here (using the above HowTo link) regarding your type of irda controller.

5. Run the following:

```
sudo depmod -a
update-modules
```

6. Restart you machine! Don't just restart X or simply log out and in again, do a full restart.

7. Once restarted and logged in, in order to receive a file then type this at the terminal:

```
ircp -r
```

To send a file use:

```
ircp <filename>
```

That's all I did.

Hope it works for you.

---

