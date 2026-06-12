---
title: "Keeping users settings after installation"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by David Brant on 2009-07-05
Hi

I have updated my / directory with a re-format and new installation from 8.10 to 9.04. I have naturally left my /home directory alone to preserve the settings of my own (initial user with admin rights) and a second standard user. My account and settings are all as were previously.

However, i am having problems re-instating the previous second user account. I get a warning when i try and set up the same username.

'Home directory already exists. Please enter a different home directory path'

I assume this is because the username already exists in the /home directory, but then again so does mine and the problem did not occur!

My username 'david' has user ID 1000 and is associated with group 'david'. The second user 'rochelle' is associated with group 1001.

I do not appear to be first able to move the contents to a temporary location before creating the 'new' account and copying them back. The only option available appears to be to delete things.

I guess i might be able to backup /home using GParted and copy back the account after deleting it, but that seems a rather roundabout way.

Any advice for a workaround would be very much appreciated.

Dave

---

