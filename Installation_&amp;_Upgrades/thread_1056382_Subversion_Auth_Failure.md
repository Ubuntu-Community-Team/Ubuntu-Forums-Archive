---
title: "Subversion Auth Failure"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by jpowellcs on 2009-01-31
I've been trying to get a SVN server running so that I can access my repo remotely, but I am getting:

svn: Authorization failed

Things I've tried:
-Adding group subversion & adding users to it
-chmod & chown the svn dirs for that group
-adding that group to authz file in svn/conf
-adding users to passwd file in svn/conf
-setting anon-access = read in svnserve.conf

Any suggestions?

---

