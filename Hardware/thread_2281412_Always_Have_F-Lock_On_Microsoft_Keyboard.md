---
title: "Always Have F-Lock On Microsoft Keyboard"
date: 2015-06-06
forum: Hardware
---

### Post by SJrX on 2015-06-06
I would like a way to always have F-Lock enabled on my keyboard so that the function keys _always_ operate as function keys.

For those of you who aren't familiar with F-Lock ([http://en.wikipedia.org/wiki/F-Lock](http://en.wikipedia.org/wiki/F-Lock)) the Function keys on your keyboard by default send silly keycodes that are meant to do things like spell check, etc... I would like them to be ignored.

I did find this article but it seemed very old, and the content didn't work for me (setkeycode just returned an error)


When I run showkey -s  I get the following output:

[FONT=Fixedsys]$sudo showkey -s
[sudo] password for sjr: 
kb mode was ?UNKNOWN?
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
# First with F-Lock off

0x1c 0x9c 
0xe0 0x75 
0xe0 0xf5 
0xe0 0x07 
0xe0 0x87 
0xe0 0x0a 
0xe0 0x8a 
0xe0 0x09 
0xe0 0x89 
0x64 
0xe4 
0xe0 0x2f 0xe0 0xaf 
0xe0 0x64 
0xe0 0xe4 
0xe0 0x0e 
0xe0 0x8e 
0xe0 0x5a 
0xe0 0xda 
0xe0 0x55 
0xe0 0xd5 
0xe0 0x39 
0xe0 0xb9 

#Now with F-lock on (these should be normal keycodes)

^[OP0x3b 
0xbb 
^[OQ0x3c 
0xbc 
^[OR0x3d 
0xbd 
^[OS0x3e 
0xbe 
^[[15~0x3f 
0xbf 
^[[17~0x40 
0xc0 
^[[18~0x41 
0xc1 
^[[19~0x42 
0xc2 
^[[20~0x43 0xc3 
^[[21~0x44 0xc4 
0x57 
0xd7                                                                                                                                                    
0x57                                                                                                                                                    
0xd7 
^[[24~0x58 
0xd8 
0x1d 
^Ccaught signal 2, cleaning up...
[/FONT]

Anyway I was wondering what the best way to fix this permanently was, I could live with it only taking effect in X.

---

### Post by SJrX on 2015-06-06
So I did try the following:

F1 down seems to be 0x3b , F1 up seems to be 0xbb

Weird F1 down is 0xe0 0x75 , Weird F1 up is 0xe0f5. 

I did try setkeycodes e075 59 and setkeycodes e0f5 187 , the first was successful the second gave the error:
KDSETKEYCODE: Invalid argument
failed to set scancode 175 to keycode 187

I am also not sure if changing this at the kernel level will change X.

---

