---
title: "Running a terminal command with an icon?"
date: 2008-09-06
forum: General Help
---

### Post by CollinT on 2008-09-06
I have installed Civ4 and it works when I use this command in the terminal

WINEDLLOVERRIDES="msxml3=n" wine "c:\program files\firaxis games\sid meier's civilization 4\civilization4.exe"

Is there a way that I can create an icon that can do the same thing.  I tried creating a launcher and putting the command above in the command field but it didn't work.

Thanks,

---

### Post by Cl0ud9 on 2008-09-06
> **CollinT said:**
> I have installed Civ4 and it works when I use this command in the terminal

WINEDLLOVERRIDES="msxml3=n" wine "c:\program files\firaxis games\sid meier's civilization 4\civilization4.exe"

Is there a way that I can create an icon that can do the same thing.  I tried creating a launcher and putting the command above in the command field but it didn't work.

Thanks,

Create a bash script and save in ~/Desktop
from the terminal: gedit filename.sh
then copy this text and save
```

#!/bin/bash

WINEDLLOVERRIDES="msxml3=n" wine "c:\program files\firaxis games\sid meier's civilization 4\civilization4.exe"

```

You might have to make it executable:
```

chmod 777 filename.sh

```

---

### Post by rossjman1 on 2008-09-06
I think you can put that line in the command parameter of the launcher.

---

### Post by CollinT on 2008-09-06
I apologize for my ignorance but could you please explain to me how to make a bash script.

---

### Post by CollinT on 2008-09-06
> **rossjman1 said:**
> I think you can put that line in the command parameter of the launcher.

I have tried that, it doesn't seem to work.

---

### Post by Cl0ud9 on 2008-09-06
> **CollinT said:**
> I apologize for my ignorance but could you please explain to me how to make a bash script.

Step 1 Open gedit:
    You can find it in Application -> Accessories -> Text Editor

Step 2: 
    Copy the text I posted previously.

Step 3:
    Save the file in /home/*yourusername*/Desktop.
    Call the file whatever you want but make sure it ends in .sh

Step 4 Make it executable:
    From the terminal:
```

cd ~/Desktop
chmod 777 *nameofthefile*

```

Then you can double-click the file from your desktop and it will run.

---

### Post by CollinT on 2008-09-06
Ok I have done everything up until step 4.  When I try to change it to an exe i get this:

chmod: invalid mode: `Civ4.sh'
Try `chmod --help' for more information.

have any ideas?

---

### Post by Cl0ud9 on 2008-09-06
> **CollinT said:**
> Ok I have done everything up until step 4.  When I try to change it to an exe i get this:

chmod: invalid mode: `Civ4.sh'
Try `chmod --help' for more information.

have any ideas?

Sorry, It should be chmod 777 Civ4.sh and not chmod Civ4.sh 777.
I'll update the previous post.

---

### Post by rossjman1 on 2008-09-06
> **CollinT said:**
> I have tried that, it doesn't seem to work.
try putting the word "env" before? Screenshot for example.

---

### Post by CollinT on 2008-09-06
Works great now thanks cloud, rossjman1 I will give your idea a try.

Just tried your idea rossjman1 and it also works great thanks.

---

