---
title: "Hardy Intellij Shortcut from sh script"
date: 2008-11-02
forum: General Help
---

### Post by wdavidow on 2008-11-02
Hey everyone.  So I've been scouring the forums, and I found a bunch of previous posts on how to create desktop/launcher shortcuts from shell scripts, but i can't seem to get it to work for intellij.

i've tried both application and application in terminal for the type, and for command i've tried 'sh -c "/usr/lib/intellij/bin/idea.sh"' i've tried just '/usr/lib/intellij/bin/idea.sh'.  I also created a launcher that re-sets my JAVA_HOME environment variable (even though it's set in my profile that gets loaded every time i sign into gnome) and attempted to use that from the launcher shortcut.  I also added /usr/lib/intellij/bin to my path so i don't even need the absolute path to use the scripts; after that i tried using just 'idea.sh' and 'ideaLaunch.sh'... I'm really at a loss here.

I should add that using either of the following commands in a terminal window works perfectly without error:

idea.sh

or

ideaLaunch.sh (this the launcher that i created that sets the JAVA_HOME variable again)

Here's the launch script that I created, just in case i have some error in here that could be causing this shortcut not work:

```

#!/bin/sh
#
# ------------------------------------------------------
#  IntelliJ IDEA Startup Script for Unix
# ------------------------------------------------------
#
#
# ideaLaunch.sh

export JAVA_HOME=/usr/lib/Java6u6
export JDK_HOME=$JAVA_HOME
/usr/lib/intellij/bin/idea.sh

```

If anyone knows what I'm doing wrong here please reply.  

Thanks for taking the time read/respond to my question :)

---

### Post by scragar on 2008-11-02
erm.. you are aware of how hopeless that second line of code is right, your setting a variable to itself, that won't change anything(and will proberly just slow things down).

Perhaphs you could go over a few things, like what happens when you go to run it, do you get an error message?

---

