---
title: "SVN Export on Ubuntu"
date: 2008-10-21
forum: General Help
---

### Post by mech7 on 2008-10-21
I am trying to export all projects in svn, I can get a list of the projects in the repository like this:

svn list [http://localhost/svn/](http://localhost/svn/)

And it will return a list like..

project_1/
project_2/
project_etc/

But now I need to do svn_export for every project like this:

svn export [http://localhost/svn/project_1](http://localhost/svn/project_1) /var/www/project_1/ --username user --password mypass --force

is there anyway to do this with bash scripting?

---

### Post by geirha on 2008-10-21
Something along these lines perhaps?
```

#!/bin/bash
url=http://localhost/svn
svn list "$url" | while read repos; do
  echo svn export "$url/$repos" "/var/www/$repos" --username user --password mypass --force
done

```
I added an echo in the loop there so it doesn't run the commands, just prints them. If it looks right, just remove the echo.

---

