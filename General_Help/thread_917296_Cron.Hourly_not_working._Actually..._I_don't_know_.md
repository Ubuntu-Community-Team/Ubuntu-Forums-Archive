---
title: "Cron.Hourly not working. Actually... I don't know much about Cron either..."
date: 2008-09-11
forum: General Help
---

### Post by _Atreides_ on 2008-09-11
Hey guys, following a lifehacker wallpaper suggestion I have a script called sunmap that i did a chmod +x on and is located in the /etc/cron.hourly directory. This is the script:

```

#!/bin/bash

wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -nc -O /home/javed/Pictures/world_sunlight_map_rectangular.jpg
```

It is supposed to download the image from the site, and as I have my wallpaper set to that image it auto updates my wallpaper. The script seems to work since when i run it separately It updates my wallpaper. It just doesn't seem to do it every hour by itself...

Now, I don't really know how to use Cron either so I am not sure what I am doing wrong. Do I have to start Cron or something before I can use it? Please help thank you for your time!:KS

---

### Post by milasch on 2008-09-11
I once struggled a bit to make my backup script to work on cron.hourly...

I ended up reading this article:
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

And figured out the way to edit the cron script is by doing:

```

crontab -e

```

not that this command will open the file by the editor found in the EDITOR variable...

to set nano as the editor, simply do:
```

export EDITOR=nano

```

---

