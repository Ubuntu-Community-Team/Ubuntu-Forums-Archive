---
title: "ASMedia ASM 1061 media controller - might it work with Ubuntu 18.04"
date: 2018-05-09
forum: Hardware
---

### Post by Hodor on 2018-05-09
My ASRock z97 Extreme 6 has an ASMedia ASM 1061 media controller, for various SATA3 devices, which plays well with Windows but I've never seen it play nicely with Linux (about the only issue I've had though, the board is otherwise excellent for both OSs).  
To boot into a linux distrubution, I first turn the controller off from the UEFI/Bios screen.  

I recently installed 18.04, using the same approach as before (turn off the ASMedia controller) bit I am now wondering if 18.04 might play better with this hardware (my DVD/CD drive connects to the motherboard via this controller, so leaving it off is possible but not ideal). I have the latest bios for the motherboard installed (2.80, 2018/3/13).
 
I've found a few previous posts on this, but none seemed to solve my problem and the messages seem a little conflicting - some people have got the media controller to work with a linux distrubution, some people seem to think the problem is the DVD drive not the media controller, not sure what to make of any of that:
[https://askubuntu.com/questions/234353/not-able-to-install-ubuntu-on-new-system](https://askubuntu.com/questions/234353/not-able-to-install-ubuntu-on-new-system)
[https://ubuntuforums.org/showthread.php?t=1905175](https://ubuntuforums.org/showthread.php?t=1905175)
[https://superuser.com/questions/363144/is-asmedia-asm1061-sata3-controller-supported-under-linux](https://superuser.com/questions/363144/is-asmedia-asm1061-sata3-controller-supported-under-linux)

I do recall when I initially built the computer the advice was to connect DVD drives to the ASMedia controlled ports, and I think when I tried connecting the drive otherwise it didn't end well; I haven't recently tried connected the DVD drive to a different SATA port.

When I tried a boot just now with the media controller on, it looked like the same old story (grub tries to start ubuntu but the system hangs indefinitely on a black screen). But when I turn off the ASMedia controller the boot process goes through fine (it's not an installation issue). 

Any advice? 

Thanks

update (the plot thickens!):
I just reconnected the DVD to one the non-ASMedia SATA ports and it works fine on ubutntu 18.04, but I can't see the drive on windows! hmm. Guess the DVD drive on this port is a windows probelm, on the ASMedia port it's a ubuntu problem.  If I can install the drive on windows on this port then I'm done, but it would be interesting to know if the ASMedia controller works with Ubuntu.
final update (solved!): now boots to ubuntu with ASMedia on (but DVD connected to a non-ASMedia / CPU sata port). Windows also now sees the drive on the new port (just needed a restart). Haven't worked out how to connect a dvd to the ASMedia controller and use it under Ubutuntu, but I don't need to do that at this stage.

---

