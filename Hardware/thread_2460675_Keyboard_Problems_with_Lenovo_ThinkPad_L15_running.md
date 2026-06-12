---
title: "Keyboard Problems with Lenovo ThinkPad L15 running Ubuntu 20.04 LTS (64 Bit)"
date: 2021-04-15
forum: Hardware
---

### Post by maik-reddiger on 2021-04-15
Hi guys, 

I already contacted Lenovo Support regarding this, but they could not help me. Here's the problem: 

At the end of 2020, I got a Lenovo ThinkPad L15. It was listed as [supporting an older version of Ubuntu]("https://certification.ubuntu.com/hardware/202006-27964"), which is actually one of the reasons why I got it, as I had been a happy Ubuntu user for years. Anyhow, Ubuntu 20.04 seems to be running just fine on it with the exception of the following issue: 

From time to time -- and I have zero idea what is causing this -- the keyboard just gets stuck / locked up. Sometimes it takes days to happen, sometimes it happens within a few minutes. It also does not seem to depend on the programs I am running, it seems to be entirely random. Basically, I am working/playing on the laptop and then suddenly the key I pressed last "gets stuck" and the keyboard does not respond any more. Other than that everything is running fine and I can still use the mouse and so on, but logging out does not resolve the issue and only a restart seems to work. 

Anyhow, Lenovo hardware support asked me to run a system check in the UEFI, but that did result in any insights. They then directed me to software support, where I spend half an hour talking to people and entering my credit card information only for them to tell me that they only provide Windows support. 

My suspicion is that the keyboard driver has a bug, but I do not know  what the driver is and where to file a bug report (I do not deal with this type of stuff usually). I have not tried  restarting the driver, as it is kinda difficult to do without a  functioning keyboard.

Any help would be gladly appreciated.

---

### Post by him610 on 2021-04-18
What happens if you connect an external USB keyboard? Do the same symptoms occur? If you don't have an external USB keyboard then forget this suggestion.

---

### Post by kurt18947 on 2021-04-18
You bought it at the end of 2020? What's the warranty situation? You might have to remove any Linux and re-install Windows for them to consider any warranty claim. If Windows does the same thing it's a hardware issue. If Windows doesn't mess up it's a Linux problem. If you have a USB keyboard you could do as suggested above. If the USB keyboard works and the integral keyboard doesn't that would point toward the integral keyboard.

---

### Post by maik-reddiger on 2021-04-20
Thanks for your responses, y'all! 

> **him610 said:**
> What happens if you connect an external USB keyboard? Do the same symptoms occur? If you don't have an external USB keyboard then forget this suggestion.

I don't have one at home, but maybe I can try next time I am at my office. Assuming I get to use it and it works, what should I type into the command line to learn more about the problem?

> **kurt18947 said:**
> You bought it at the end of 2020? What's the  warranty situation?  

I have warranty on the hardware. As I said, I already contacted Lenovo about the issue, in their view there is no issue with the hardware. 

> **kurt18947 said:**
> You might have to remove any Linux and re-install  Windows for them to consider any warranty claim.  


[LIST=1]
[*]My warranty is on the hardware, not the software. I actually tried software support and even sent them the money, but then, as you correctly presume, they told me they only do Windows support. 
[*]I have a somewhat elaborate setup, reinstalling the OS is something I am trying to avoid as much as possible. 
[/LIST]

> **kurt18947 said:**
> If Windows does the  same thing it's a hardware issue. If Windows doesn't mess up it's a  Linux problem.

Sorry, the price I have to pay for trying this approach is too high. 

> **kurt18947 said:**
> If you have a USB keyboard you could do as suggested  above. If the USB keyboard works and the integral keyboard doesn't that  would point toward the integral keyboard.

Yes, but, as far as I can tell, I still would not know whether it's hardware or software-related. I already know it's the keyboard, for it is the only thing not working.

---

### Post by maik-reddiger on 2021-04-22
So today it happened while I was in the office, the backspace got stuck  (a particularly gnarly one). So I plugged in the USB keyboard, and I was  actually able to use it. There was no more backspace input. However,  the built-in keyboard remained unresponsive.

---

### Post by maik-reddiger on 2021-04-30
So I found this post: 

[https://unix.stackexchange.com/questions/478638/laptop-keyboard-drivers-event-handlers-in-linux](https://unix.stackexchange.com/questions/478638/laptop-keyboard-drivers-event-handlers-in-linux)

and, after fiddling around a bit to find the right event, I ran the following command: 
```
sudo evtest event3
```
Here are the first few lines of the output (the remaining ones just list the keys and the testing): 
```
Input driver version is 1.0.1
Input device ID: bus 0x11 vendor 0x1 product 0x1 version 0xab54
Input device name: "AT Translated Set 2 keyboard"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 1 (KEY_ESC)
    Event code 2 (KEY_1)
    Event code 3 (KEY_2)
...
```

So it is indeed the "AT Translated Set 2 keyboard", driver version 1.0.1. I googled it but could not figure out where to file a bug report. Can anyone please tell me?

---

### Post by maik-reddiger on 2021-06-14
Just in case this affects someone else and that person stumbles over this thread: I filed a bug report for the keyboard driver, which is available here:
[https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.8/+bug/1930745](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.8/+bug/1930745)

---

### Post by maik-reddiger on 2021-11-04
Unfortunately, the bug is still unresolved, though it has been confirmed now. If you are experiencing the same bug, try to close and open the laptop. For some reason that seems to resolve it for me without having to restart.

---

