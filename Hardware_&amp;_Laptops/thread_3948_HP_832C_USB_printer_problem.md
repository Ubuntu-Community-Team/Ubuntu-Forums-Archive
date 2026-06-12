---
title: "HP 832C USB printer problem"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by Caudata on 2004-11-10
I just tried to install my HP 832C. Everything looks good, but nothing will print. I look in the printer section under system configuration and my printer was automatically detected while connected via USB. I hit the print test page option in properties under the connection tab and nothing prints. I did notice when I first reboot and I try to print under connections and I use print test page the status will say "printing". I then get tired of waiting for 3 minutes and hit cancel jobs. If I then hit print test page again under the general tab status will read "USB busy will try again in 30 seconds" and will continue to say that message any time there after. I've done the forum search and tried some of the suggestions,but so far nothing has worked.  I'd appreciate any help that can be provided, thank you in advance, later!

                                                                                                    -Caudata

---

### Post by Caudata on 2004-11-10
I just noticed something else. Under printers in the system configuration everything is detected as it should be. When I "print test page" and check on the job and look at it's properties the connection is  "network printer-CUPPS". Then I try to switch it back to loacl printer and it won't switch. Meanwhile under system configuration it still says local printer and detected correctlly. I have no clue, thanks for any help!

                                                                                                    -Caudata

---

### Post by randy on 2004-11-11
Delete the network printer and add it as a local usb printer using gnome-cups-manager.  (The printing icon in the gui menu).

---

