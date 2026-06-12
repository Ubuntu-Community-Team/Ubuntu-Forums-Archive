---
title: "subversion send mail after commit"
date: 2008-11-20
forum: General Help
---

### Post by mitjab on 2008-11-20
i search but i did not find any topic about this.

How to make that subverison will send mail after comiit to some users?

---

### Post by rudy.elgato on 2008-11-20
Have a look at the [hook-scripts]("http://subversion.tigris.org/tools_contrib.html#hook_scripts") link on [http://subversion.tigris.org/tools_contrib.html]("http://subversion.tigris.org/tools_contrib.html").  There are plenty of templates there that hopefully will give you some ideas to do what you need to do.

Good Luck...

---

### Post by mitjab on 2008-11-20
Thx you
will try

---

### Post by rudy.elgato on 2008-11-20
I don't use automatic email notification in svn myself, but a quick look at that information and quick googling around makes me think that:

1. your SVN repository will have a ./hooks directory.
  
2. your SVN installation will have delivered commit-email.pl script.  I'm at work right now and the CentOS system I use has this commit-email.pl script installed in /usr/share/doc/subversion-1.1.4/tools/hook-scripts.  Your commit-email.pl script is probably in a different directory, so you'll need to find it.

3. back in your SVN/hooks directory you will need a file called 
post-commit (no extension) which should look similar to:

#!/bin/sh

REPOS="$1"
REV="$2"

/full/path/commit-email.pl "$REPOS" "$REV" -s SVN:project-name [email]user1@.abc.net[/email] [email]user2@.abc.net[/email]...


So you'll need the /full/path to your commit-email.pl script.  Your SVN/hooks directory probably already has a post-commit.tmpl script.  You can probably just copy that to your post-commit script.  Mine has an extra line that runs a log-commit.py script, but think that could just be commented out.

Hope this helps.

---

