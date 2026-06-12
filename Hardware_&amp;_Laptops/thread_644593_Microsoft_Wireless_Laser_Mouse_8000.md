---
title: "Microsoft Wireless Laser Mouse 8000"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by furriner on 2007-12-19
I am considering buying a Microsoft Wireless Laser Mouse 8000, which is a Bluetooth mouse. My existing Bluetooth mouse didn't work very well with Ubuntu 7.10. Has anyone tried the MS Wireless Laser Mouse 8000 with the latest release of Ubuntu and does it work properly? Thanks.

---

### Post by furriner on 2007-12-19
> **furriner said:**
> I am considering buying a Microsoft Wireless Laser Mouse 8000, which is a Bluetooth mouse. My existing Bluetooth mouse didn't work very well with Ubuntu 7.10. Has anyone tried the MS Wireless Laser Mouse 8000 with the latest release of Ubuntu and does it work properly? Thanks.

My last Microsoft Intellisense Bluetooth mouse, which sadly died, did not work with Ubuntu, and that puts me off buying the Microsoft Wireless Laser Mouse 8000. Has anyone used other MS Bluetooth mice with Ubuntu 7.10 and got them working? Is Bluetooth under Ubuntu reasonably working and stable? I just get the general picture that stuff which works easily under Windows is a real pain to get working with Linux.

Comments please?

---

### Post by Melsion on 2007-12-20
Hi! Just today I got my brand new Laser Mouse 8000 and got it to work without a problem. Althought I must say the extra buttons will take some research to get them working (I think editing the .Xmodmap file should be enough), primary buttons, wheel and volume controls are enough for me to get going.

Someone posted the steps to get a bluetooth mouse working under ubuntu, but just in case:
- press your mouse "connect" button to make it "visible"
- in your favorite console: "hcitool scan"
it should give you the names and addresses of all your bluetooth devices, in my case the mouse was called "microsoft", the "0a:1b:2c:3d:4e:5f" thing is the device address, copy it and:
- in your console "sudo hidd --connect paste-here-the-mouse-address"
now the mouse should just work (it did for me), if not, repeat the last step making sure the mouse is in "pairing mode", in this mouse, the led blinking in green and red alternatively indicates that, also check you copied the address correctly.
- if it worked edit /etc/default/bluetooth and make sure these lines match:
BLUETOOTH_ENABLED=1
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
HIDD_OPTIONS="-i --connect paste-here-the-mouse-address --server"

and that should do it, the next time you restart your pc the mouse should connect automatically (restarting just /etc/init.d/bluetooth should do the trick too).

I'll see about the extra buttons as soon as can, anyone has done something similar to point me in the right direction?

---

### Post by taekr on 2007-12-23
I'm using Microsoft Wireless Laser Mouse 8000.. it works perfectly in Ubuntu 7.10. Ubuntu got it right in the first place.  

But I haven't figured out how to enable 5 buttons.. tought..

---

