---
title: "How to check the printer status from command line?"
date: 2014-10-14
forum: Hardware
---

### Post by uqbar on 2014-10-14
I have my Ubuntu Server acting (also) as a print server with CUPS.
All printers are networked and accessed through the "socket://some_addr:9100" URI.
I'd need to create a script to check by command line whether each and every printer has ran out of paper or ink or has a paper jam.
Is there any way to do it?

---

### Post by Frogs Hair on 2014-10-14
This might be worth reading.  [http://www.techrepublic.com/article/control-printers-in-linux-from-the-command-line/](http://www.techrepublic.com/article/control-printers-in-linux-from-the-command-line/)

---

### Post by tgalati4 on 2014-10-14
There are several HP utilities that can give status information:

```
apropos hp
```

There are some supplies switches in *lpadmin*, but I don't know how to use them:

>       -o cupsIPPSupplies=true

       -o cupsIPPSupplies=false
            Specifies whether IPP supply level values should be reported.

       -o cupsSNMPSupplies=true

       -o cupsSNMPSupplies=false
            Specifies whether SNMP supply level (RFC 3805) values should be reported.


```
man lpadmin
```

A google search found these:

[http://libinklevel.sourceforge.net/#what_to_do](http://libinklevel.sourceforge.net/#what_to_do)  and the CLI that uses this library: [http://ssnjara.wordpress.com/2011/10/08/ink-checking-the-ink-level-of-your-printers-from-cli/](http://ssnjara.wordpress.com/2011/10/08/ink-checking-the-ink-level-of-your-printers-from-cli/)

Looks like it only works for locally-connected devices, not networked devices.

In regards to the *lpadmin* options, if your printer supports it, you can check:

```
grep Supplies /etc/cups/ppd/*.ppd
```

Setting to *true* should put levels in your /var/log/cups log files.

---

