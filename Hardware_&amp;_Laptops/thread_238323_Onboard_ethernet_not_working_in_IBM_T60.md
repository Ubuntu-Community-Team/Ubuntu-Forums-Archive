---
title: "Onboard ethernet not working in IBM T60"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by khaoohs on 2006-08-17
The wired ethernet adapter in my IBM  T60P does not work. The wireless was picked up fine as eth1, but the only other network adapter is l0.

As a linux newbie I would appreciate any help in this matter.

---

### Post by indigoshift on 2006-08-17
Interesting.  I had the opposite problem with an old G40:  wired was connected almost instantly, but eth1 needed fiddling with every time I tried to go wireless--with mixed results.

---

### Post by khaoohs on 2006-08-19
Further research shows that there is some type of error with the actual ethernet adapter.

[INDENT]Ethernet: I noticed a problem with the e1000 module, you&#8217;ll notice the following in the syslog:
e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
e1000: probe of 0000:02:00.0 failed with error -5

This means the checksum in PCI data area is not ok. It seems the windows driver does not have this problem because it does not verify the checksum at all. Of course you could work around the problem by disabling the e1000_validate_eeprom_checksum in e1000_main.c but that&#8217;s a nasty workaround. I found a workaround for this without having to touch kernelsource: just set &#8220;Internal Network Device: Hidden&#8221; in the BIOS. If you reboot again you won&#8217;t have a network card of course, but after re-enabling it again in the BIOS the module should work without any problems then.[/INDENT]
Found at [http://64.233.161.104/search?q=cache:k21Hzrr2JWEJ:michael-prokop.at/blog/2006/07/02/thinkpad-t60-laptop-with-debiangrml-linux/+ubuntu+ethernet+t60&hl=en&gl=us&ct=clnk&cd=1&client=opera]("http://64.233.161.104/search?q=cache:k21Hzrr2JWEJ:michael-prokop.at/blog/2006/07/02/thinkpad-t60-laptop-with-debiangrml-linux/+ubuntu+ethernet+t60&hl=en&gl=us&ct=clnk&cd=1&client=opera")

And ever further research finds this: [http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid]("http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid")

---

