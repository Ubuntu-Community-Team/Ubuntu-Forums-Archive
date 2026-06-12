---
title: "Launcher/Terminal help."
date: 2008-10-04
forum: General Help
---

### Post by eagledrc on 2008-10-04
Hey,

I installed Google Chrome on wine, but it only works when I enter ```
wine ~/.wine/drive_c/windows/profiles/$USER/Local\ Settings/Application\ Data/Google/Chrome/Application/chrome.exe --new-http --in-process-plugins
``` in a terminal, and it launches on the wine hq home page.  When I copy that into a launcher command, it launches Chrome, but it starts on about:blank, and it can't connect to the internet.  What I want to do, is create a launcher, and that command launches an excutable text file, which launches a terminal and automatically launches Chrome from that terminal.  Of course, it would be nice to not have to run Chrome from a terminal, but is there anyway I can make this work???

Thanks,

David

---

### Post by jamesrl on 2008-10-05
If you install [crossOver Chromimum]("http://www.codeweavers.com/services/ports/chromium/") (still essentially running google chrome from wine) it will have shortcuts by default.  Not 100% sure why wine worked differently depending on how you launched it, so can't help you there.

---

