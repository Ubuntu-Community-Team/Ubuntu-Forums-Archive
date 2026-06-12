---
title: "how do i enable multi pointer xorg?"
date: 2008-11-28
forum: General Help
---

### Post by vbman11 on 2008-11-28
Hi guys and gals!

so I was looking around the Internet randomly and stumbled upon MPX. MPX is a module in X that lets one have multiple cursers controlled by multiple mice. Then I tried to find how to enable it, and I figured out that I only have to use the following commands to start using it...

```

xinput --list --short
xinput --create-master "foobar"
xinput --reattach "MyMouse" "foobar pointer"
xinput --reattach "MyKeyboard" "foobar keyboard"

```

...but the only one that xinput accepts is the first one.

Please help me.:(

---

