---
title: "Laptop turns on back when trying to shut down or sleep"
date: 2017-03-09
forum: Hardware
---

### Post by ndd12 on 2017-03-09
Hello, I have Ubuntu 16.04.2 LTS (dualboot with Windows 8.1 Pro) on my laptop HP Probook 650 G1 (i5-4200M, 8GB RAM, 128GB SSD). Almost everything is working fine except turning laptop off. System shuts down normally, without any error and soon powers off. But, after maybe 4 or 5 seconds later it powers on by itself and continuing to boot normally. Same with sleep. At this moment to really power off my laptop, i have to shut down ubuntu, wait until it powers on again (or just simply reboot), boot to windows and shut down as always. So i guess its not really hardware problem. And maybe what is important, its not rebooting. It shuts down completely, LEDs are off, fan stops, dvd tray wont open. But starts again after a few seconds like after pressing power button. Normal reboot happens without cutting off power, just reloads.

Dont know really what to with that. 


Sorry if I described problem with a little bit of chaos, but English is not my native language, but im doing my best! :)

---

### Post by Paddy Landau on 2017-03-09
I had the same problem a few years ago with an HP laptop. But it happened with both Windows and Linux. It was still under guarantee, and the HP technical team confirmed that it was a hardware error. They replaced my machine.

So, I'm quite confused that it works with Windows but not with Ubuntu.

Open a terminal (press Ctrl+T) and enter the command:
```
sudo shutdown -h now
```
What happens?

---

### Post by ndd12 on 2017-03-10
I figured out that problem exist only when laptop is connected to a docking station. But still its only on Ubuntu. Shutdown command which you posted doesnt change anything, when connected to a docking station it shuts down and powers on a few seconds later.

---

### Post by Paddy Landau on 2017-03-10
All right. Two more suggestions, although I'm pretty much grasping at straws, sorry.

**First suggestion**

Try this command and tell us what happens.
```
sudo systemctl poweroff
```

**Second suggestion**

Use [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key") (well, in this case, it's actually REISUO).

[LIST=1]
[*]Log out of your session, so that you go back to the login screen.
[*]Press the following key-combinations, in order.
[LIST=1]
[*]Alt+PrtScrn+R
[*]Alt+PrtScrn+E (then wait one or two seconds)
[*]Alt+PrtScrn+I (then wait one or two seconds)
[*]Alt+PrtScrn+S
[*]Alt+PrtScrn+U
[*]Alt+PrtScrn+O
[/LIST]
[/LIST]
At this point, the machine should quickly shut down.

If it still reboots after REISUO, it probably means that there's something quirky about the hardware, and the manufacturer has catered for that with some driver in Windows.

---

### Post by ndd12 on 2017-03-14
Both method failed - i mean, laptop went off and on after a few seconds. What else I have checked: Unplugged everything from docking station except power supply - no change. Also I unplugged laptop from station just after shutting down (before it powered on again), during shutdown etc - laptops boots again even when disconnected from station. I have to firstly disconnect laptop from station and then initialize shut down (no matter how) - no self-start after that.

And of course no problem like that from Windows (checked even Windows 7 from other hdd). So i think it have to be software problem somewhere in Ubuntu.

Aaand I don't think it is fixed by some sort of driver in Windows, because when I installed vanilla Windows 7 (from msdn, not from HP install dvd) with completely no drivers (except of course drivers supplied with windows), plugged laptop into docking station, checked if battery started to charge (yes, so electrically it worked) and shut down system. It did not start again on its own.

---

### Post by Paddy Landau on 2017-03-14
Well, sorry, I just don't know what to say now. I've never come across this problem where Ubuntu has this error but Windows doesn't.

What happens if you boot from a Live CD and then shut down — does the laptop still restart?

If a Live CD (or Live USB) can shut it down, then there may be a fault with the shutdown script in Ubuntu, and that's not an area with which I'm familiar. But if the Live CD still restarts, it could be that the built-in Linux driver thinks that the hardware is something different. What you could do is make a Live CD of a non-Ubuntu distribution, for example [Manharo]("https://manjaro.org/"), and see if that also has the problem.

It's a difficult one, this.

---

### Post by ndd12 on 2017-03-19
I did more tests, all performed on other hdd, and here are results:
I tried Ubuntu 16.04 (again, fresh install, to eliminate some configuration fail), Manjaro, openSuse and Debian. All of them both from LiveCD and after Install. All distros behaved in same way: from LiveCD they were able to shut down properly but after install all boot up again.

Well, at this moment i think i'll give up. Spend way to much time on this, now i'm just disconnecting laptop from station before shut down, and thats it...

---

