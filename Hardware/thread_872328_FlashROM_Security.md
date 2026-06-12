---
title: "FlashROM Security"
date: 2008-07-27
forum: Hardware
---

### Post by yangandjiao on 2008-07-27
Fusion devices have an on-[chip]("http://www.chinaicmart.com/") Advanced Encryption Standard (AES) decryption core, combined with an
(R)
enhanced version of the Actel Flash-based lock technology (FlashLock ). Together, they provide
unmatched levels of security in a programmable logic device. This security applies to both the FPGA core
and FlashROM content. Fusion devices use the 128-bit AES (Rijndael) algorithm to encrypt programming
files for secure transmission to the on-chip AES decryption core. The same algorithm is then used to
38
decrypt the programming file. This key size provides approximately 3.4 x 10  possible 128-bit keys. A
computing system that could find a DES key in a second would take approximately 149 trillion years to
crack a 128-bit AES key. The 128-bit FlashLock feature in Fusion works via a FlashLock security Pass Key
mechanism, where the user locks or unlocks the device with a user-defined key. 
If the device is locked with certain security settings, functions such as device read, write, and erase are
disabled. This unique feature helps to protect against invasive and noninvasive attacks. Without the
correct Pass Key, access to the FPGA is denied. In order to gain access to the FPGA, the device first must be
unlocked using the correct Pass Key. During programming of the FlashROM and/or the FPGA core, you can
generate the security header programming file, which is used to program the AES key and/or FlashLock
Pass Key. The security header programming file can also be generated independently of the FlashROM and
FPGA core content. The FlashLock Pass Key is not stored in the FlashROM. 
Fusion devices with AES-based security allow for secure remote field updates over public networks such as
the Internet, and ensure that valuable intellectual property (IP) remains out of the hands of IP thieves.
Figure 3 shows this flow diagram.

---

### Post by tamoneya on 2008-07-28
was this supposed to be a question.  It appears as if you just copied and pasted from some website.

---

