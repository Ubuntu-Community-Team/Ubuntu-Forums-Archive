---
title: "Configuring keyboard hotkeys with same scancodes and different keysyms"
date: 2016-03-10
forum: Hardware
---

### Post by pilleo19 on 2016-03-10
I have a bluetooth keyboard [Samsung bkb10]("http://www.samsung.com/us/support/owners/product/BKB-10USWEGXAR").  It is keyboard for andoind mainly, so it does not have alt,  super(winkey), f1-f12, menu, but has lots of hotkeys(most of them work  nice under linux). But some hotkeys are not working, and I want to make  thems to behave as alt, f1-f12, menu. Also i want hotkeys functions too,  so i would love to make smth like Fn button for hotkeys. Well, that is  all i want. At least i need alt,super,menu and f1-f12, could not imagine  it is so hard without them under linux.  So, i was trying to use keytouch - no luck. It is able to read correct keysym, but keytouch-editor saves only part  of it into its keyboard files, and it appears that needed keys are same  for keytouch too. Anyway i did not see it works for me at all, even with  with many keys acting the same way. Right now keys that i want to make  as Alt, super, menu, do not work at all, have same scancodes, but have  different keysyms:
  xev  shows same thing for some hotkeys, that do not work :
  ```
KeyRelease event, serial 39, synthetic NO, window 0x5400001,
root 0xf5, subw 0x0, time 12647284, (224,225), root:(224,253),
state 0x0, keycode 248 (keysym 0x0, NoSymbol), same_screen YES,
XLookupString gives 0 bytes: 
XFilterEvent returns: False

```  But kacpimon can recognize their keysyms and that they are different keys:
  ```
Input Layer:  Type: 4  Code: 4  Value: 787205
Input Layer:  Type: 1  Code: 240  Value: 0
Input Layer:  Sync
Input Layer:  Type: 4  Code: 4  Value: 787207
Input Layer:  Type: 1  Code: 240  Value: 1
Input Layer:  Sync

```  Same as getscancodes:
  ```
787205 (0xc0305)
787205 (0xc0305)
787207 (0xc0307)
787207 (0xc0307)

```
 sudo evtest /dev/input/evt14 output for same keys:

  ```
Event: time 1457614378.384393, type 4 (EV_MSC), code 4 (MSC_SCAN), value c0305
Event: time 1457614378.384393, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 1
Event: time 1457614378.384393, -------------- SYN_REPORT ------------
Event: time 1457614378.384420, type 4 (EV_MSC), code 4 (MSC_SCAN), value c0305
Event: time 1457614378.384420, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 0
Event: time 1457614378.384420, -------------- SYN_REPORT ------------
Event: time 1457614378.681877, type 4 (EV_MSC), code 4 (MSC_SCAN), value c0307
Event: time 1457614378.681877, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 1
Event: time 1457614378.681877, -------------- SYN_REPORT ------------
Event: time 1457614378.775600, type 4 (EV_MSC), code 4 (MSC_SCAN), value c0307
Event: time 1457614378.775600, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 0
Event: time 1457614378.775600, -------------- SYN_REPORT ------------

```
  As you can see scancodes are same even in kacpimon, but keysyms are different in kacpimon, getscancode, evtest for every single key, but not for xev  and other tools.  Also i think that getscancodes actually is showing keysyms, but not  scancodes for them. I know that xmodmap is old and i should not use, and that i should xkb. I  was able to find some answer that could help me, if i wasn't noob - [Custom keyboard layouts: adding a character for which no keysym is defined]("http://askubuntu.com/questions/429946/custom-keyboard-layouts-adding-a-character-for-which-no-keysym-is-defined") Also that link might be usefull but it is outdated, so i cannot check it-[Don't use showkey or xev -- use udev and evtest instead.]("http://unix.stackexchange.com/a/130762/160491")
  But i cannot do it with xkb or xmodmap, i just cannot understand how.  Please help me, working on it for 3 full days and still did not find  any solution... Thank you very much! 
     
[URL="http://askubuntu.com/questions/744256/configuring-keyboard-hotkeys-with-same-scancodes-and-different-keysyms"]
link to the same topic on askubuntu with answer[/URL]

---

