---
title: "Sound card not detected toshiba satalite"
date: 2010-04-18
forum: Hardware
---

### Post by Havoc805 on 2010-04-18
I have scanned these forums quite a bit and there is no fix to my problem.  After i upgraded ubuntu to 9.1 i lsot alll sound and the detection of my on board audio.

I have a satallite a135.  Sound did work in previous ubuntu versions.

I have tried most fixes, and nothing works.  Most cite downloading things from asla sight but its no longer up.  Please help or let me know of a distro that actualy works.

---

### Post by ajgreeny on 2010-04-18
Are you sure the sound card is not detected?  Sow the output of ```
sudo aplay -l
```which will show what is seen by the OS.

---

### Post by lidex on 2010-04-18
Have you worked through the known karmic issues here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Still no sound? Can you post the output of these terminal commands for me:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

### Post by JulioGee on 2011-05-26
I have the same problem on a toshiba a135-s2286.
ive been trying to fix this for days now.
i just cant seem to find a solution.
my soundcard is not in my hardware or even detected by my operating system.


helppppp meeeeeeeeee..:(

---

