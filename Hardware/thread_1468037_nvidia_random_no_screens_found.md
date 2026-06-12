---
title: "nvidia random no screens found"
date: 2010-05-01
forum: Hardware
---

### Post by padrik on 2010-05-01
Hi,

I have this annoying issue with my gigabyte something board with an on-board GeForce 7100 / nForce 630i. I've installed 10.04 ( 9.10 had similar issues ) with the latest nvidia driver. Now 2 out of 3 times the system boots and stops in the "can't load driver and I'm going in low res mode" screen. Reason in the log "no screens found".

So, I choose to go to the console and restart gdm and X starts without problems in Hi res. *&$%@**&&&F*&k&%@$nnnnnn and more harsh terms.

That is 2 out of 3 times so sometimes it boots ok in HiRes. It appears that the nvidia driver loads before X so I've put crap like rmmod nvidia && modprobe nvidia in the gdm start script without result. I've put Option	"UseDisplayDevice" "DFP" in the device section of /etc/X11/xorg.conf without result. I've put Options BusID "PCI:0:10:0" in xorg.conf because lspci told me that without result.

What did make a difference was to edit rc.local with
mknod -m 0666 /dev/nvidiactl c 195 255
mknod -m 0666 /dev/nvidia0 c 195 0
as the first error in gdm was that it could not find /dev/nvidiactl during boot.

Also, when I look in /lib/modules/<kernel>/modules.alias I see that the nvidia aliases cannot be found in  /usr/share/jockey/modaliases/nvidia-current although that should be solved according to some posts

alias pci:v000010DEd00000E00sv*sd*bc04sc80i00* nvidia_current
alias pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00* nvidia_current
alias pci:v000010DEd*sv*sd*bc03sc02i00* nvidia_current
alias pci:v000010DEd*sv*sd*bc03sc00i00* nvidia_current

So what is going on, why does this behavior occurs 2 out of 3 times during boot and does not occur at all when I start gdm directly from console.

These problems did not occur with ubuntu 9.04. 

Kind regards.

P

---

