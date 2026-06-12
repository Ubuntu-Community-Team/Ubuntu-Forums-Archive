---
title: "GLXCreateNewContext with prime-select intel"
date: 2017-05-18
forum: Hardware
---

### Post by vimsical on 2017-05-18
I have a system with on-board intel graphics and couple of nvidia cards for compute. I wanted to use the Nvidia cards strictly for compute. So I selected:
```
prime-select intel
```

And it works. Displays are connected to the on-board video output ports. But when I check glxinfo, I got this error message:
```
$ glxinfo 
name of display: :0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  37
  Current serial number in output stream:  38

```

Any ideas?

---

