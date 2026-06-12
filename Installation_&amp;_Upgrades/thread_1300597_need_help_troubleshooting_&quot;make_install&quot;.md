---
title: "need help troubleshooting &quot;make install&quot; for ir-kbd-i2c and hauppauge remote control"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by kurtkimber on 2009-10-25
I'm wondering if someone can walk me through troubleshooting the following "make install" problem. Let me know what other debugging info is needed.  Thanks in advance.

I'm currently running this linux kernel:
  Linux htpc 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64 GNU/Linux

I'm trying to get a hauppauge remote control working in mythtv (v 0.21) using this ir-kbd-i2c approach:
  [http://rtr.ca/hvr1600](http://rtr.ca/hvr1600)

I follow the instructions on this page, but have the following error when I execute the "sudo make install" command:

```
sudo make install
...
cp hauppauge_remote.conf /usr/local/bin/
chmod 0644 /usr/local/bin/hauppauge_remote.conf
/usr/local/bin/enable_hauppauge_remote.sh
FATAL: Error inserting ir_kbd_i2c (/lib/modules/2.6.28-16-generic/extra/ir-kbd-i2c.ko): 
  Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
```Then dmesg shows:

```
...
[ 1974.505118] ir_kbd_i2c: Unknown symbol ir_codes_empty
[ 1974.505376] ir_kbd_i2c: Unknown symbol ir_codes_rc5_tv
[ 1974.505528] ir_kbd_i2c: disagrees about version of symbol ir_input_init
[ 1974.505531] ir_kbd_i2c: Unknown symbol ir_input_init
[ 1974.505712] ir_kbd_i2c: Unknown symbol ir_codes_fusionhdtv_mce
[ 1974.505890] ir_kbd_i2c: Unknown symbol ir_codes_pv951
[ 1974.506249] ir_kbd_i2c: Unknown symbol ir_codes_hauppauge_new
```

---

