---
title: "Palm no longer syncing... ttyUSB1 no longer exists"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Dougga on 2008-01-05
Hello,
I installed Ubuntu late last year and have been using kpilot to sync my Palm treo 700p.
I tried it recently and Ubuntu no longer recognizes the Treo.  I checked /var/log/messages and find that it no longer finds the device on ttyUSBx.  It did a couple of days ago.

Take a look:   This is what it used to do... when it worked
Jan  2 12:59:46 jasper kernel: [ 6022.358766] usb 1-2: new full speed USB device using ohci_hcd and address 19
Jan  2 12:59:46 jasper kernel: [ 6022.580742] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
Jan  2 12:59:46 jasper kernel: [ 6022.580807] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB3
Jan  2 13:00:17 jasper kernel: [ 6052.417764] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jan  2 13:00:17 jasper kernel: [ 6052.417852] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jan  2 13:24:13 jasper kernel: [   24.953980] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1


Now... it's not working...
Jan  5 12:35:35 jasper kernel: [ 1557.600178] usb 1-2: new full speed USB device using ohci_hcd and address 13
Jan  5 12:37:47 jasper kernel: [ 1688.122358] usb 1-2: USB disconnect, address 13


I don't be3lieve I've changed anything other than installing updates that have been released.  Would the updates break my palm functionality?

Thanks for any assistance

---

### Post by Dougga on 2008-01-05
Not relevant to the problem above but...

I find it amazing that I can find no way of subscribing to my own thread.
Why does Ubuntu make this process so difficult?
I have to search for my threads each time I come to this site?

Update: The only way I can find to subscribe to a thread is to edit my own post.  Who thinks up these designs... they should be slapped.

---

