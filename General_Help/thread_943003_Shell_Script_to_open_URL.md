---
title: "Shell Script to open URL"
date: 2008-10-09
forum: General Help
---

### Post by wah fun on 2008-10-09
I am a noob to Linux and am looking to get my feet wet with scripting. I want to write a simple script to open a specific URL and put an icon on the desktop that can be clicked to execute the script. (Sorry, but I did this in a batch file in windows and am trying to do the same thing in Linux. My wife is accustomed to this and so, there ya go.)

Thx 4 ur hlp.

---

### Post by PhrankDaChickenGeek on 2008-10-09
You can just open up Firefox, browse to the URL, then drag the little icon next to the URL to your Desktop to do this.

Or create a file, make it executable, and use the following code

```

$ touch url.sh
$ chmod a+x url.sh
$ gedit url.sh

```

url.sh:
```

#!/bin/sh

firefox http://google.com

```

---

### Post by wah fun on 2008-11-12
Thanks. It works. I am still learning scripting.

---

