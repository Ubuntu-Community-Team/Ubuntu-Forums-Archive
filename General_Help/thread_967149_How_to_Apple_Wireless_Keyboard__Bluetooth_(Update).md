---
title: "How to: Apple Wireless Keyboard / Bluetooth (Update)"
date: 2008-11-01
forum: General Help
---

### Post by DaveBear on 2008-11-01
I can't get an Apple wireless keyboard to work with my new ASUS Eee PC 1000H in either Windows XP or Ubuntu mode. The directions posted at [http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673) looked promising - until I encountered something different.

It asks me to do the following:

Change "HIDD_ENABLED=1" to "HIDD_ENABLED=0". Take care that using this how-to you do not need any "--connect BD_ADDR" parameters to hidd. So you can remove them from HIDD_OPTIONS. "HIDD_OPTIONS='--master --server'" is just fine.

On my computer, that particular file reads "HID2HCI_ENABLED=1", not "HIDD_ENABLED=1". I changed it to 0 anyway, and when that didn't work, I changed it back to 1 and tried it again, with the same results.

If I type in sudo hidd --search, it returns...

sudo: hidd: command not found

If I type in sudo hid2hci --search, it returns...

hid2hci: unrecognized option '--search'

Can anyone who's solved this same issue tell me how you fixed it? If you haven't dealt with this issue, can you offer any suggestions for experiments based on the code I posted above? I'm not used to working with a terminal, so I'm not really sure what's going on.

---

