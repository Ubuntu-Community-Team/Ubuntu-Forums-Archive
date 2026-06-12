---
title: "LCD display DE-LD011 and LCD4Linux"
date: 2011-02-24
forum: Hardware
---

### Post by bachenke on 2011-02-24
Hi,

I've bought a small lcd-display (2x16) from eBay. It's a DE-LD011 made by Sure Electronics.

LD4Linux is the software I was planning on using. Although, after hour of trying i still can't get the thing to work.

The display is supposed to be supported through the MatrixOrbital driver according to LCD4Linux.

I've complied LCD4Linux-0.11.0-SVN from source and then make and make install. So far so good.

Wrote the /etc/lcd4linux.conf
```

Display DE-LD011 {
Driver 'MatrixOrbital'
Model DE-LD011
Size 2x16
Port '/dev/bus/usb/003/002'
Speed 9600
Contrast 160

}

Widget CPU {
class     'Text'
expression    uname('machine')
prefix    'CPU '
width 9
align    'L'
update    tick
}

Layout Default {
Row1 {
Col1 'CPU'
}
}


Variables {
tick    500
}

Display 'DE-LD011'
Layout 'Default'
```

When I try to start lcd4linux I get the following print out:

```
name@localhost:/usr/local/bin$ lcd4linux -Fvv
Version 0.11.0-SVN-965 starting
plugin_cfg.c: Variable tick = '500' (500)
lcd4linux.c: initializing driver MatrixOrbital
MatrixOrbital: $Rev: 840 $
MatrixOrbital: Display:DE-LD011.Model '0' is unknown from /etc/lcd4linux.conf
```

Has anyone tried LCD4Linux? Anybody know what I've done wrong?

I'm on 10.10 Maverick Meerkat...
******[]("http://ssl.bulix.org/projects/lcd4linux/attachment/wiki/Download/lcd4linux-0.11.0-SVN.tar.bz2")**

---

### Post by howefield on 2011-02-25
Moved to  "*Hardware & Laptops* " where you are likely to get more help than in Tutorials & Tips.

---

