---
title: "Accessing Bitlocker disk from Ubuntu"
date: 2020-08-31
forum: Hardware
---

### Post by parol00 on 2020-08-31
Hello, I just switched from Windows to Ubuntu. Next to C I had disk d encrypted with bitlocker. C was completely deleted because I switched to ubuntu, but I did not touch d. It looks d(bitlocker) in ubuntu right now but I can't access it. What should I do ? note: I know my Bitlocker Password but I don't have a recovery key. Better explain it as simple as possible, because I don't speak English. Thanks. (I used translation, sorry.)

---

### Post by TheFu on 2020-09-01
No direct experience, but google found a few options to do this.  

At my reading, most of the options seemed a little "iffy" and heavy on marketing. They may not work.  Regardless, I'd probably plan on wiping my system after using any of those solutions if they aren't in the Canonical software repos already. Software designed for people desperate often take advantage of their overwhelming need to get data back.

Dislocker doesn't look too bad, but it doesn't appear to work always.

A few google results:
[https://github.com/Aorimn/dislocker](https://github.com/Aorimn/dislocker)
[https://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts](https://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts)

The best answer may be to boot into Windows, somehow and use the native tools to back up that data to non-encrypted storage. After all, everyone needs backups, but most especially when encryption is required on portable computing devices.

On Linux, we'd use LUKS for encrypting block storage, then use different file systems on top of that, depending on how much flexibility in the future resizing the file systems will likely need.

---

### Post by mastablasta on 2020-09-02
if you don't have the key, how do you expect to unlock the data? one of the issues with encrypted data. and if they can be decrypted without the key, then why would you use the service anyway? it would be pointless.

password is likely for the key. though i guess it also depends how you set it up.

[https://en.wikipedia.org/wiki/BitLocker](https://en.wikipedia.org/wiki/BitLocker)

---

### Post by TheFu on 2020-09-02
I thought MSFT kept a copy of the key automatically in their cloud if you ever used an email address, like they pushed for hard, to setup the account.  But I have to say, I don't know because when MSFT started pushing that, I stopped using Windows. To me, the reason to use encryption is privacy - that includes privacy from MSFT.

Anyone using encryption needs to have excellent backups, period.

---

### Post by mastablasta on 2020-09-03
> **TheFu said:**
> 
Anyone using encryption needs to have excellent backups, period.

they started pushing bitlocker on work laptops. my first question was what happens if disk is damaged, what is the backup. they said "you have to take care of that". so i left mine unlocked (for now). Sure the one drive is an option, but i also use that on work phone (where they also set large portion of internal memory as encrypted container for email and one drive). On work phone there is one drive installed. what happens if i "backup" 250 GB to it? and then we have questions like " why do you need so much data?" and similar.

if you have encrpytion you need to have unencrypted backup at secure location. or backup can be encrypted but you have to make sure you can unlock it no matter what.

---

### Post by TheFu on 2020-09-03
All portable devices should have full drive encryption for any storage routinely on-the-move.

Whether backups should or should not be encrypted is a local decision.  While I don't currently encrypt backups, I know that I should.  I would use LUKS below the file system, at the partition level, to accomplish that. Mainly because LUKS supports multiple unlock keys/methods (8-slots), so I can use a convenient, but secure 2FA challenge-response most of the time, but also have key-file and huge-ass random key as backups.  So, if there is an issue with the key-file or the 2FA device gets lost, I don't lose access to the data.  

I also know that LUKS is self-contained. There's no hidden, extra, anything stored some magical place inside the OS.   If I have the disk and know any of the unlocking keys/passphrase/challenge, when that storage is connected to another Linux system with dm-crypt + LUKS installed, it can be unlocked.  I know this because I've done it many times with a USB SSD.

If I were on Windows, I'd probably use Veracrypt.  OTOH, I wouldn't use Windows.  I'm lucky in that I control the IT choices for my work.

---

