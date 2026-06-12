---
title: "[SOLVED] Basic Bash Shell Script help"
date: 2008-10-19
forum: General Help
---

### Post by Jonny0204 on 2008-10-19
I have the following script below and I am having problems copying a bunch of files over to my iphone. U can see that the mp3s are located in the folder '/iPhone Sync' and i want to copy them to the location on my iphone, using ssh, which is '/var/mobile/Media/Music/'.

As my bash script knowledge is very limited, i'm stuck :(

So my problem, just to make it totally clear is: Transfer multiple mp3s to iphone from that iPhone Sync folder, using ssh.

```
#!/bin/sh
echo "iPhone Sync beginning"
echo "..."
ssh jonny@jonny-laptop cat < "/home/jonny/Music/iPhone Sync/" ">" "\*"
echo "please enter password"
ssh root@192.168.0.18 cat < "/home/jonny/Music/iPhone Sync/" ">" "/var/mobile/Media/Music/*"
echo "transferring ..."
echo "..."
echo "...done!"
exit 0
```

---

### Post by geirha on 2008-10-19
Redirecting directories will not work at all. Try scp
```
scp -r "/home/jonny/Music/iPhone Sync/"* jonny@jonny-laptop:"/var/mobile/Media/Music/"
```

Should recursively copy all files in "/home/jonny/Music/iPhone Sync/" on the local computer, to "/var/mobile/Media/Music/" on jonny-laptop with user jonny

---

### Post by Jonny0204 on 2008-10-19
thats exactly what i wanted thankyou :), except the code was:

```
scp -r "/home/jonny/Music/iPhone Sync/"* root@192.168.0.18:"/var/mobile/Media/Music/"
```

I probs didn't make that too clear in my question. Anyways thank you.

---

