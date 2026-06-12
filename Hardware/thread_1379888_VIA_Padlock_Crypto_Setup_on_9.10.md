---
title: "VIA Padlock Crypto Setup on 9.10"
date: 2010-01-13
forum: Hardware
---

### Post by tji on 2010-01-13
I just set up a VIA C7 based system with MythBuntu 9.10, and spent some time to get the "Padlock" crypto acceleration feature of the CPU working.

I modified /etc/ssl/openssl.conf based on what I read in an archived thread ( [http://ubuntuforums.org/showthread.php?t=710243](http://ubuntuforums.org/showthread.php?t=710243) ).    After moving the padlock lines around in the config file a bit, I get it to work so openssl uses padlock by default:

```
type             16 bytes     64 bytes    256 bytes   1024 bytes   8192 bytes
aes-128-ecb      98844.07k   366726.80k   989248.18k  1617129.21k  2011497.24k
```

I thought that by enabling padlock in openssl, SSH would automatically use it, but by SSH performance still seems the same, ~8MB/s.    

Anyone else using padlock and done any SSH configuration?

---

