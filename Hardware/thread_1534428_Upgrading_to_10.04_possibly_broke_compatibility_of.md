---
title: "Upgrading to 10.04 possibly broke compatibility of libdc1394 and libftdi"
date: 2010-07-19
forum: Hardware
---

### Post by ilganeli on 2010-07-19
Hello, not sure whether this is the right place to post but since I feel that my issue is with the hardware drivers for these devices I am throwing it up here.

Background:
I am coding in C++ on the newest 32-bit version of Ubuntu and I am using the libraries libdc1394 and libraw1394 to talk to a Point Grey Bumblebee stereo camera. I am also using the libftdi library to talk to a set of DX-12 servo motors via a 232R FTDI USB-Serial converter chip. Before upgrading to 10.04, in version 9.1?? of Ubuntu I was able to use both these libraries concurrently without any issue. 

However, after upgrading, I am no longer able to open a USB connection to the servo motors if I link both the dc1394 and ftdi libraries and then call the method, dc1394_new() in my code.

For instance :

```
ServoController(){
Ftdi:Context ftdiComm;
ftdiComm.open(PARAM1, PARAM2, PARAM3);
}
```

```
int main(){
ServoController *cont = new ServoController();
cont->doStuff();

//dc1394_t *connected = dc1394_new();
} 
```


Works while 

```
int main(){
ServoController *cont = new ServoController();
cont->doStuff();

dc1394_t *connected = dc1394_new();
}
```

crashes at run-time with a seg fault some ways down from the call to ftdiComm.open(). I am unable to post a stack trace at the moment but the crash is at the method "register_platform" in 
I believe "control.c" which I am unable to open. 

I have tested the libraries individually and have had no issues whatsoever running them alone. This issue only appears and the above case is the simplest example that I can provide. Please note that I have also attempted to use the libftd2xx library and received the exact same error. I have not yet attempted to revert to Ubuntu 9 but I have tried with a fresh install of Ubuntu 10, which did not help. I would like to avoid reverting to Ubuntu 9 if at all possible because I really do not want my only recourse to be working on an obsolete version of the OS.

Please let me know if anyone has any suggestions or thoughts on the matter or knows a better place to post this question. Thank you.

---

### Post by ilganeli on 2010-07-20
bump

---

### Post by ilganeli on 2010-07-22
Reverting to 9.1 solves the issue but this doesn't help me much.

---

