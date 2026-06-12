---
title: "Trying to make sense of Wireless"
date: 2009-06-30
forum: Hardware
---

### Post by ammonbirk on 2009-06-30
So I have a HP Pavilion Dv6000 and I cant make Ubuntu recognize my wireless according to an earlier post I need to use this link [http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads) but I honestly cant make any sense of this. Can anyone please give me a comprehensive overview? or can I just run Linux through Sun's virtualbox. I'm pretty new to this so i would appreciate simple terms. Thanks

---

### Post by cariboo on 2009-06-30
It would help if we knew what wifi chipset your laptop uses. Could you open an Application-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will list your network hardware and write it to a text file called network,txt, you can copy the file to your windows partition and paste it in your next post.

---

