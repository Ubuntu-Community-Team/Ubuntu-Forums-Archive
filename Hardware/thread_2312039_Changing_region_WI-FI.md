---
title: "Changing region WI-FI"
date: 2016-02-01
forum: Hardware
---

### Post by victor70 on 2016-02-01
Good afternoon. Do you can help with the following problem? After entering the command
```
iw reg set BO
```

if you look through the team
```
iw reg get
```

the region is set correctly, but as soon as the interface including command
```
ifconfig wlan0 up
```

when viewing
```
iwconfig
```

For a few seconds I see that option maxtp = 30 db, and then goes to 20 db. After that, I check the region with the command
```
iw reg get
```

I see that the region was replaced with the BO to RU
I faced somebody with such a problem that occurs? Can anyone suggest what can you do?

---

