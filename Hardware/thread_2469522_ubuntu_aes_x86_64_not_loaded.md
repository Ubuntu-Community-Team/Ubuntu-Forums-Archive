---
title: "ubuntu aes_x86_64 not loaded"
date: 2021-12-01
forum: Hardware
---

### Post by chpnp on 2021-12-01
Hi there,

I received a new disk i consider to encrypt. I wanted to check what the toll would be.
i found that  aes_x86_64 is not not loaded (ubuntu 20.04).
I am not litterate enough to understand if this should be solved somehow, anyone can give me some hint ?

thanks


Command line output :

[B]$ sort -u /proc/crypto | grep module
module       : aesni_intel
module       : ccm
module       : cmac
module       : crc32_pclmul
module       : crct10dif_pclmul
module       : cryptd
module       : ecdh_generic
module       : ghash_clmulni_intel
module       : kernel
$[/B]


i checked that after reading this page : [https://www.cyberciti.biz/faq/how-to-find-out-aes-ni-advanced-encryption-enabled-on-linux-system/](https://www.cyberciti.biz/faq/how-to-find-out-aes-ni-advanced-encryption-enabled-on-linux-system/)
where i see the output from the same command is slightly different:

[B]module       : aesni_intel
module       : aes_x86_64
module       : crc32_pclmul
module       : crct10dif_pclmul
module       : ghash_clmulni_intel
module       : kernel[/B]

---

### Post by TheFu on 2021-12-02
If you use dm-crypt with LUKS, I bet it will all "just work."  LUKS is the native Linux encryption. Everything else is non-native.

To create/setup a new LUKS container, use **cryptsetup** - that's the name of the program and the package.
My laptop which uses whole disk encryption isn't on now and it is located in a different room, and doesn't run 20.04, so I cannot check which modules are loaded. Sorry.
If you want to setup whole disk encryption that includes the OS, then it is easiest to just check the box during the installation.  Retro-fitting any encryption for the OS post-install is non-trivial.  I've never done it.

If you just want to encrypt a data area, then doing that after the fact is fairly easy with cryptsetup.  [https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it/](https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it/) has beginner-friendly instructions.

---

### Post by chpnp on 2021-12-09
I have both / and /home luks-encrypted.
Mty question was whether there was ay feature requiring additional enablement....

---

### Post by TheFu on 2021-12-10
> **chpnp said:**
> I have both / and /home luks-encrypted.
Mty question was whether there was ay feature requiring additional enablement....

**Any feature**?  Yes. You cannot do file-based backups from a different boot OS without manually decrypting first.

But if you have those mounts automatically happening at boot (probably via the crypttab) with the decryption happening pre-boot, then almost everything (99.9%) will work fine.

---

