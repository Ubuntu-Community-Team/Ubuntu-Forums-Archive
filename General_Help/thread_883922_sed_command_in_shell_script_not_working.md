---
title: "sed command in shell script not working"
date: 2008-08-08
forum: General Help
---

### Post by surfer63 on 2008-08-08
I have the following line in a config file:
#define INSTALL_XRC_DIR "/Users/Shared/development/hugin_related/hugin/mac/ExternalPrograms/repository/arch/ppc/share/hugin/xrc/"

Note that it is one line even though the forum might break it.

I want to change that to #define INSTALL_XRC_DIR ""

Please note that the part "/Users/Shared/development/hugin_related/hugin/mac/ExternalPrograms/repository/arch/ppc/share/hugin/xrc/" can change depending on the system
I tried to use sed for that from a shell script. I tried
sed 's/INSTALL_XRC_DIR.*$/INSTALL_XRC_DIR ""/g' "file_in" > "file_out"

I also tried without g or sed -e ...
I tried a couple of other options but nothing seens to work.

Please help.

---

### Post by croto on 2008-08-08
Hi

I tried your command and it works fine here. Could you please post exactly the command you used with the filenames? As a side note, you should make sure the config file doesn't have any other instance of INSTALL_XRC_DIR, since it would replace any following characters on that line by "".

---

### Post by surfer63 on 2008-08-08
The point is not that it doesn't work from the command line, because that's where I tested it. Than I copied it inside my shell script. And it doesn't work from within the shell script.

#####

#!/bin/sh

... some more stuff ...
sed 's/INSTALL_XRC_DIR.*$/INSTALL_XRC_DIR ""/g' "config.h.pre" > "config.h
"
... more stuff where I need the above result ...

---

### Post by surfer63 on 2008-08-08
I feel very stupid. I've got a couple of directories in my script and it was  executing the sed command in the wrong directory.

So, it does function.

---

