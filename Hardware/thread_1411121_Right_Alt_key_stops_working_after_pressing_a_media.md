---
title: "Right Alt key stops working after pressing a mediakey, Ubuntu 9.04"
date: 2010-02-19
forum: Hardware
---

### Post by KaffeeJunky on 2010-02-19
Hello,
I'm using a g15 keyboard on an 9.04 AMD64 Ubuntu
everything worked fine until I did update my BIOS, I have an M2N32-SLI Deluxe Mainboard from Asus.
Since the BIOS update I'm having a strange problem, whenever I press a media key on my g15 keyboard the right alt key get's kinda unmapped, switching the keyboard layout fixes it until I press a media key again.

Here's the xev output I get when pressing a media key  
> 
KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  46  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
when the xev windows had focus 
and this without focus on the xev window
> 
MappingNotify event, serial 46, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 46, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247
if you need any futher information let me know it.


Edit: My Kernel Version: 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:40:19 UTC 2010 x86_64 GNU/Linux

---

