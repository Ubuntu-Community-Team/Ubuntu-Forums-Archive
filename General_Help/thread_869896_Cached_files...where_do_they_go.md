---
title: "Cached files...where do they go?"
date: 2008-07-25
forum: General Help
---

### Post by leveliv on 2008-07-25
When you are using foresay the  update manager..it says  "Files will be cached locally" Where are they kept? ....and how do I clean that out once and a while...cause I have been losing stupid amounts of space and I think that might be why, Is there a hard drive cleanup program?

---

### Post by jeroen.kurvers on 2008-07-25
[FONT=Courier New]Those files are downloaded to /var/cache/apt/archives/. 
To clean the cache you can use the following commands: sudo apt-get clean and sudo apt-get autoclean.
[/FONT]

---

