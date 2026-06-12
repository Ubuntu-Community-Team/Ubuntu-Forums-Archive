---
title: "Ubuntu 11.x, Trendnet KVM and numlockx"
date: 2012-01-24
forum: Hardware
---

### Post by tleish on 2012-01-24
There's been a long standing issue with Ubuntu 11.x, Trendnet KVM switches and using Numlock key no longer works in toggling the KVM switch.

I did read about the workaround to switch to the console, and then you could use the standard keyboard shortcuts to toggle the KVM switch (See: [http://beitis.net/ubuntu-kvm-switches-and-scroll-lock/](http://beitis.net/ubuntu-kvm-switches-and-scroll-lock/)), but this solution takes too long back and forth.

I then found if you installed numlockx
```
sudo apt-get install numlockx
```

I can then setup a bash script shortcut on my desktop that executes the command to toggle the KVM:
```
#!/bin/bash
numlockx off; sleep 1;  numlockx on; sleep 1; numlockx off
```

Is it possible to map the numlock key on my keyboard to a numlockx command so I can just use the keyboard instead of the shortcut command?  I've googled around for a bit and couldn't find a solution.

---

### Post by tleish on 2012-01-24
I've figured out a solution, in case anyone is interested:

1. Install numlockx
```
sudo apt-get install numlockx
```

2. Create a script on desktop (KVM.sh)
```
#!/bin/bash
numlockx on;
sleep 1; 
numlockx off;
sleep 1; 
numlockx on
```

3. Create a custom keyboard shortcut to point to KVM.sh script (I used the key <SUPER>+K to execute this script)

---

### Post by cong06 on 2012-03-20
Thank you!

Can you mark this as solved?


I also invite you to provide this solution for others at askubuntu.com (since that's the first search result):
[http://askubuntu.com/questions/67769/using-numlock-for-trendnet-kvm-switch-no-longer-works](http://askubuntu.com/questions/67769/using-numlock-for-trendnet-kvm-switch-no-longer-works)

---

### Post by blackcatt on 2012-03-23
Could you please write in more details how to &#65279;create a keyboard shortcut to point to the script?

---

### Post by cong06 on 2012-03-24
- Write the script with gedit. Save.
- Right click on the file, and go to properties. Change to the permissions tab, and check Execute for at least "Owner".
- Open up Keyboard Shortcuts (in unity search for keyboard, and choose "keyboard" not "Keyboard layout", I'm unsure the method without unity)
- Go to the shortcuts tab. choose "Custom Shortcuts"
- click the "+" button. choose a name, and find the path to the file (you can get the path from the file properties)
- Now that the command is "installed", set a keyboard shortcut


Was that detailed enough?

---

### Post by blackcatt on 2012-03-24
Thank you very much for the explanation. I tried the solution and got the NumLock blinking when hit the shortcut, but this didn't make kvm to switch..(Ubuntu 11.04 64bit Classic desktop). Trendnet TK214i
The following script works fine for me:
#!/bin/bash
xset -led named "Scroll Lock";
sleep 1;
xset led named "Scroll Lock";
sleep 1;
xset -led named "Scroll Lock"

---

### Post by kysdaddy on 2012-11-01
> **cong06 said:**
> - Write the script with gedit. Save.
- Right click on the file, and go to properties. Change to the permissions tab, and check Execute for at least "Owner".
- Open up Keyboard Shortcuts (in unity search for keyboard, and choose "keyboard" not "Keyboard layout", I'm unsure the method without unity)
- Go to the shortcuts tab. choose "Custom Shortcuts"
- click the "+" button. choose a name, and find the path to the file (you can get the path from the file properties)
- Now that the command is "installed", set a keyboard shortcut


Was that detailed enough?

Running kubuntu and this worked great for me.
Searched keyboard, opened custom shortcuts and then just followed the instructions.

Thanks

---

### Post by livinjean on 2013-01-04
Just fyi..

I am using Rosewill RKV-2U switch between WinXP & ArchBang.

tleish's solution (comment # 2), worked perfectly for me.

P.S. sorry if this comment on an old thread causes unwanted notification for someone, but I thought it might be helpful for anybody who lands here via google.

---

### Post by kysdaddy on 2013-03-21
> **kysdaddy said:**
> Running kubuntu and this worked great for me.
Searched keyboard, opened custom shortcuts and then just followed the instructions.

Thanks


OK I just moved to Ubuntu 12.10 (clean install) so I had to do this again, this time I had to use /system settings/keyboard/shortcuts/custom shortcuts and xbindkeys config to get it working.

I created the shortcut in keyboard and then got it working with xbindkeys.:P

---

