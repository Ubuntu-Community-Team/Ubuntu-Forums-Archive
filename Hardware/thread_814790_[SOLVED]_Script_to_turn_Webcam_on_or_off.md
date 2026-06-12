---
title: "[SOLVED] Script to turn Webcam on or off"
date: 2008-06-01
forum: Hardware
---

### Post by DavidFromCanada on 2008-06-01
I need help.
I want to create a script similar to those that turn compiz on or off.
I need to execute 
```
flashcam -qD
```
If that is running I need to execute
```
killall flashcam
```
I have something started but it won't work
```
#!/bin/sh

# click to start, click to stop
if flashcam; then
 killall flashcam
else
 flashcam -qD
fi
```

It's simply thing that that I don't know how to do any help is appreciated.

David

---

### Post by sdennie on 2008-06-01
It sounds like you are looking for a toggle script.  This should do it:

```

#/bin/bash

if ! pgrep $1 > /dev/null ; then
    exec $@
else
    pkill $1
fi

```

If you run it as:

```

the_script flashcam -qD

```

It should do what you want.

---

### Post by DavidFromCanada on 2008-06-01
Thanks for your help.

---

