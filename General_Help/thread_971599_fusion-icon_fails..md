---
title: "fusion-icon fails."
date: 2008-11-05
forum: General Help
---

### Post by jarl on 2008-11-05
Hi.

I just got fusion-icon recomended to swith compiz on/off.

So I did a 'sudo apt-get install fusion-icon'
then 'fusion-icon -n' but it fails with

```

 * Detected Session: kde
 * Searching for installed applications...
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'

```

Jarl, a Kubuntu convert

---

