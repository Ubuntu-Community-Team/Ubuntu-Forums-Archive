---
title: "Confused about memory max for my laptop Dell E6420"
date: 2021-02-03
forum: Hardware
---

### Post by bobnutfield on 2021-02-03
Hello Everyone

Just thought I'd get an experienced opinion about the maximum memory that can be installed in my old laptop.  It's an old i5 and the business I usually buy my memory from says that the maximum memory that can be installed is 8GB.  However, when i run

```
sudo dmidecode -t memory | grep -i max
```

i get this:

```
Maximum Capacity: 16 GB
```

If I could install another 8GB it would help a lot.  But, I don't want to waste money if it isn't likely to work.

Any thoughts about the conflict?

Thanks for any replies.

Bob

---

### Post by mikewhatever on 2021-02-03
I don't know if this is related to Ubuntu. There is also no way for anyone to know for sure, given the available info. 
You had better look for the manual of the exact model, and check the specs.

---

### Post by Autodave on 2021-02-03
Everything that I find says that 8G is max.  2x4

---

### Post by bobnutfield on 2021-02-04
Thank you for the replies.  I'm aware that factory specs say that 8GB is the max.   But, in searching for an answer I found a number of old Dell forums where people have successfully installed 16GB in this particular laptop model.  However, it came in both i5 and i7 processors, both specs called 8GB the max.  On these forums, the mother board (Sandy Ridge, I think) was described as supporting 16GB.

My question was why this terminal command listed 16GB as the max.  I assume that command gets its information directly from the mother board and memory controller.  I've never known it to give an incorrect reading when run as sudo, but I could me wrong.

If I can find some cheap memory I might try it.  As I understand, if I install more than the max memory the worst that can happen is that it won't get past POST until I put the correct memory back in.  If anyone knows why I would get an incorrect output from that command I'd like to understand.

Many thanks

Bob

---

### Post by corradoventu on 2021-02-05
See Dell support site: [https://www.dell.com/support/home/en-lt/product-support/product/latitude-e6420/docs](https://www.dell.com/support/home/en-lt/product-support/product/latitude-e6420/docs)
[https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6420_owner%27s%20manual_en-us.pdf](https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6420_owner%27s%20manual_en-us.pdf)
[https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6420_setup%20guide_en-us.pdf](https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6420_setup%20guide_en-us.pdf)

---

### Post by bobnutfield on 2021-02-06
Thank you, I have all that documentation.  My question was why DMIDECODE reports 16GB as the maximum since it gets it information from the mother board.

Regards

Bob

---

