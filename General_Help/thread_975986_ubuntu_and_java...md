---
title: "ubuntu and java.."
date: 2008-11-08
forum: General Help
---

### Post by stangkid4 on 2008-11-08
I can't seem to install java on my ubuntu. I just installed it yesterday for the first time and I get alot of error codes and things. for example when I try to install limewire it says something about dkpg and something but oh well. how can i install java?

---

### Post by taurus on 2008-11-08
How did you install java yesterday?  What's the output of this command from a terminal?

```
java -version
```

To install Sun's java, you can do, from a terminal

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

