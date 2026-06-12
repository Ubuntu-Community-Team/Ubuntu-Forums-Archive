---
title: "need help w. bash/Nautilus script"
date: 2008-10-23
forum: General Help
---

### Post by akahige on 2008-10-23
I have a bash/Nautilus script to chmod selected files that I cobbled together from various tips and posts.

```
#!/bin/bash
gksudo -u root -k -m "root password is required to change owner/permissions:" /bin/echo "Do you have root access?"
quoted=$(echo -e "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | awk 'BEGIN {FS = "\n" } { printf "\"%s\" ", $1 }' | sed -e s#\"\"##)
eval gksudo chmod 644 $quoted
exit 0

```

The "quoted" variable comes from [g-scripts](http://g-scripts.sourceforge.net/faq.php), and is intended to handle file names with spaces.

It works fine, but I'd like it to do more: What I'd like to achieve is to be able to set permissions recursively and have the directories be the default 755 (so either change or preserve). Just adding "-R" to the chmod command didn't work, and I don't know enough about what I'm doing to troubleshoot it.

Can anyone help...?

---

