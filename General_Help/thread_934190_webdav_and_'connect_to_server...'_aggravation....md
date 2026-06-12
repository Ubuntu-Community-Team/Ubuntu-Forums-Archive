---
title: "webdav and 'connect to server...' aggravation..."
date: 2008-09-30
forum: General Help
---

### Post by yrrej on 2008-09-30
Hi,

I recently enabled a webdav 'share' on one of my computers ( a mac ).

When I use the "Connect to server..." item under the Places menu I
can connect to the webdav share. 

A window is opened which displays the contents of the share and
an icon is placed on the desktop with a title
       "webDAV on mbp".

My complaint is that the desktop icon is useless. If one double
clicks on the rascal a dialog appears that asserts that the share
is not a webdav object. The icon also appears in the sidebar of
any filebrowser and gives the same result when clicked.

Seems to me that clicking the icon ought to cause a window displaying
the share to be shown.

I suspect the clicking the icon generates a try to open the root
directory on the httpd server instead of the actual share.

Should this be considered a "bug"?

Jerry

---

