---
title: "[SOLVED] Big Firefox Problem"
date: 2008-10-13
forum: General Help
---

### Post by tdashroy on 2008-10-13
Okay so I recently got into Ubuntu and have been trying to learn shell commands and how to write scripts and whatnot. I was following this guide I found online linuxcommand.org. I was attempting to run this script and store its output into a file. Then, after I did that I attempted to open up the file, which was supposed to be an html file, in firefox. I used the following command.

```
sudo firefox page
```

I typed in my password and it told me that I needed to close firefox for this to work. So I did so not thinking anything of it, and then tried again. About 10 lines popped up in the terminal telling me certain variables were made, and then firefox opened with my page, except it was blank. I figured I just made a mistake somewhere and went to check my script to make the file, and my file that the script made. Both were empty. So I though I may have chosen to output the script to a file wrong and opened firefox back up to retrieve the author's version of the script to compare, and my firefox opened up to a blank page(I have it set to open up whatever previous tabs I had open when I closed it). I tried going to google, it worked, but in the address bar i noticed it didn't say http:\\[www.google.com](www.google.com), but rather just google.com like I typed in. I searched something in google and after it brought up the results I was unable to go back, as in the back button was not highlighted. I looked at my history, and nothing was stored. I checked the preferences and it showed that it would store history for at least 90 days. All of my bookmarks are gone too. 

Umm...yea sorry for the long post but I have no idea what to do. I did a complete removal of firefox and reinstalled it through synaptic, but the same thing still happens. As I am typing this right now, it still says google.com in my address bar(because i searched ubuntuforums from google). If there is any more info needed please let me know.


EDIT: wow, epic fail on my part. will use gksudo next time lol.

```
sudo chown -R <user_name>:<user_name> ~/.mozilla
```

Thanks to this post [http://ubuntuforums.org/showthread.php?t=801136](http://ubuntuforums.org/showthread.php?t=801136)
Sorry bout posting this when it was already taken care of =/.

---

