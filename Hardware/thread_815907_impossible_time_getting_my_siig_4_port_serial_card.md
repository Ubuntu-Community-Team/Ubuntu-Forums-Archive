---
title: "impossible time getting my siig 4 port serial card working..."
date: 2008-06-02
forum: Hardware
---

### Post by andrew davidoff on 2008-06-02
hello all,

i'm hoping someone can help me.  i just purchased a siig cyberserial 4s card and although as far as i can tell ubuntu server 8.04 is recognizing it, i can't get any input on any of the 4 ports.  these 4 are in addition to the 2 on my motherboard, which work fine.

i have been reading faqs and manuals and what not all afternoon and for the most part it has just made me dizzy.

i have recompiled my kernel and set CONFIG_SERIAL_8250_RUNTIME_UARTS to 6.  at boot i see the os recognize all 6:

[   43.489121] Serial: 8250/16550 driver $Revision: 1.90 $ 6 ports, IRQ sharing enabled
[   43.489277] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.489560] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.491185] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.491833] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.492198] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.492611] ttyS4: detected caps 00000700 should be 00000100
[   43.492621] 0000:02:04.0: ttyS4 at I/O 0x8800 (irq = 16) is a 16C950/954
[   43.493222] ttyS5: detected caps 00000700 should be 00000100
[   43.493231] 0000:02:04.0: ttyS5 at I/O 0x8808 (irq = 16) is a 16C950/954
[   43.493829] ttyS2: detected caps 00000700 should be 00000100
[   43.493839] 0000:02:04.0: ttyS2 at I/O 0x8810 (irq = 16) is a 16C950/954
[   43.494459] ttyS3: detected caps 00000700 should be 00000100
[   43.494469] 0000:02:04.0: ttyS3 at I/O 0x8818 (irq = 16) is a 16C950/954

setserial is installed and configured as follows:

/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
/dev/ttyS1 uart 16550A port 0x02f8 irq 3 baud_base 115200 spd_normal skip_test
/dev/ttyS2 uart 16950/954 port 0x8810 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS3 uart 16950/954 port 0x8818 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS4 uart 16950/954 port 0x8800 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS5 uart 16950/954 port 0x8808 irq 16 baud_base 115200 spd_normal skip_test

minicom allows me to open devices 0 and 1 and use them perfectly.  it also allows me to open devices 2 through 5, but i seem to only be able to send traffic, not receive (according to /proc/tty/driver/serial).  also according to /prod/tty/driver/serial, i see CTS on the one pci card port that has something connected at the moment (a cisco switch using the cisco blue rollover cable).

as far as software, i have tried:

* fiddling with setserial configuration, including adding ^fourport and trying to let it autoconfigure and auto_irq

* looking at port addresses and irqs with lspci -vv: lspci shows different port addresses for 3/4 the ports and different irqs for 1/2 the ports as does dmesg, so i tried using those, but those definitely don't work (setserial takes a while to configure them with the alternate settings, and minicom hangs on exit)

as far as hardware, i have tried:

* moving a known good serial connection (tested on ttyS0) to all 4 ports, to confirm i don't just have my ports mixed up

* trying a straight cable instead of a rollover

any help you can provide is appreciated.  i'm sure there's something simple i'm not understanding or not doing correctly, but at the moment i'm totally at a loss.

thanks.
andrew davidoff

---

### Post by andrew davidoff on 2008-06-02
i have also...

* checked out my BIOS (set to automatically assign resources)
* played with minicom settings (speed, flow control, etc)
* confirmed what setserial thinks the ports are set to using it with -g and -a, compared to other working ports (looks the same less UART style)
* read parts of the serial howto at tldp.org

andrew davidoff

---

### Post by andrew davidoff on 2008-06-03
i have also...

* made a loop back plug for pins 2 and 3 and confirmed that i do see what i type in minicom, with local echo and flow control off, on all ports with the plug in.
* tried changing the default card port voltage from 0v to 5v and 12v with on change

andrew davidoff

---

