---
title: "temporary workaround for cpu overheat problem"
date: 2010-02-26
forum: Hardware
---

### Post by AlmaTlust on 2010-02-26
Just to let everyone know that I found a (temporary) solution for my laptop cpu overheat problem:
- instal cpulimit from the repositories.
- find out the pid of the process that takes too much cpu and overheats the computer
- hit ALT-F2 (at leat in kde, I think gnome is the same), type "cpulimit --pid=YOURPROGRAMSPID --limit=(highest percentage the process should be allowed to take), hit enter, and your done.

It is very helpful especially with programs that run in the background and take a lot of cpu power, but don't need to run very fast (like encoding videos, nepomukservices etc.) I can now run my system at performance mode with full cpu power and not fear it might overheat again...

Hope that helps anybody else with cpu overheat problems.

---

