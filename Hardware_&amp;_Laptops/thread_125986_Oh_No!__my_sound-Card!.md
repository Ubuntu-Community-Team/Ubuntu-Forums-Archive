---
title: "Oh No!  my sound-Card!"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by annie on 2006-02-05
Hello everyone, I having problem with sound-Card.  I have soundblaster16 sound-Card but it is not working I do not know Why.  It was worked ago when I first Configured it but it is not longer.  This is what I Tried:

sudo modprobe snd-sb16
alsamixer
nano /etc/modules
    snd-sb16

There is a problem with the Last Step because no /modules folder.  Is instead something like /modutils I do not know Why.

Please Help me get this to Work!

P.S. I am Sorry for my English it is bad but I am Learning how to Speak more correct.

---

### Post by Lord Illidan on 2006-02-05
Did you install new software or something? If so, what did you install?

---

### Post by annie on 2006-02-05
[QUOTE=Lord Illidan]Did you install new software or something? If so, what did you install?[/QUOTE]

What Kinds of software are you speaking of?  I have many music players to try out was installed.  Is This what you are Talking of?

---

### Post by mztriz on 2006-02-05
Could you post the output of this 
dmesg | grep -i "isa\|multi\|sound\|audio"

---

### Post by annie on 2006-02-05
[QUOTE=mztriz]Could you post the output of this 
dmesg | grep -i "isa\|multi\|sound\|audio"[/QUOTE]

Oh My!  That turned out oddly.

[  144.731866] Disabled Privacy Extensions on device c02eb280(lo)
[ 2854.551287] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 2854.634437] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 2855.235156] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 2855.302166] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 2855.548458] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 2855.668351] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 2855.804274] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 2855.887441] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 3049.980057] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 3050.079528] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 3051.416899] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 3051.516090] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 3986.319199] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 3986.439853] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4405.614508] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4406.552396] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4406.708496] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4406.808365] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4406.883297] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4406.992377] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4407.052367] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4407.142948] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4407.192263] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4407.319843] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4408.232479] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4408.323008] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4476.581027] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4476.697062] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4476.774145] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4476.839311] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4476.927094] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4476.992232] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 4477.069299] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 4477.152956] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5657.711232] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5657.787794] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5657.841111] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5657.933863] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5658.317444] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5658.419350] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 7418.474837] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 7418.586261] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 7418.695449] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 7418.783753] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 7419.247401] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 7419.335698] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 7419.432058] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 7419.541170] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 7420.191662] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 7420.303052] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[18821.208726] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[18821.363288] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[21158.634402] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[21158.829190] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).

---

