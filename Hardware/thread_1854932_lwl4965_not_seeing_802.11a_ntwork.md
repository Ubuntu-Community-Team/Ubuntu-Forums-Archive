---
title: "lwl4965 not seeing 802.11a ntwork"
date: 2011-10-05
forum: Hardware
---

### Post by dod1450 on 2011-10-05
I have seen many discussion on network issues on not connecting. But I have not seen anything that can help on why my intel 4965 under Unbutu 11.04 not seeing any 802.11a 5ghz wifi.  
   I changed my hardrive from Ubuntu 11.04 native OS to a Windows XP native and with Windows it is able to see my four 802.11a network SSIDs.  But when I exchanged my disk with Ubuntu 11.04 I do not see any of my four 802.11a 5ghz SSIDs.

    I am able to connect to my other 802.11 B/G/N 2.4 ghz network with no problems.  I am stump. My laptop is a Lenovo T61 Type 7658  

   Thank you for reading this,

---

### Post by jawilljr on 2011-10-05
The iwl4965 5ghz bug was fixed with [this patch](http://kernel.opensuse.org/cgit/kernel/commit/?id=aac11c1b351413aa3412e258e2b2dcba31777209). And according to that patch you need kernel version 2.6.39 or greater.

The way I see it you have 3 choices:

1. Upgrade the kernel.
2. Wait about a week and install Oneiric 11.10.
3. Install the latest compat-wireless.

I know that install compat-wireless fixes it because it fixed my iwl4965 5ghz.

Jerry

---

### Post by dod1450 on 2011-10-11
I had finally found kernel 2.6.39 , 2.6.39-020639-generic #201105190911 ,(which was not easy) My 4965 now sees all my 5 ghz network,

  Thank you

---

