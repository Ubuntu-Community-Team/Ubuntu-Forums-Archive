---
title: "Missing memory please help!!!!!!!!!!!!"
date: 2008-11-13
forum: General Help
---

### Post by AZorin on 2008-11-13
I have ubuntu and gparted says that the partition has about 1gb free but nautilus and df say that I only have about 500mb free. I also have an ext3 partition about 600 mb and I used 197mb but nautilus says I've used the whole partition. I know that ext3 reserves 5% but not 50%! How do I get back all that missing memory. CAN SOMEONE PLEASE HELP ME!!!!! I don't think I have ever had this problem before.:cry::frown::confused:

---

### Post by oilchangeguy on 2008-11-13
> **AZorin said:**
> I have ubuntu and gparted says that the partition has about 1gb free but nautilus and df say that I only have about 500mb free. I also have an ext3 partition about 600 mb and I used 197mb but nautilus says I've used the whole partition. I know that ext3 reserves 5% but not 50%! How do I get back all that missing memory. CAN SOMEONE PLEASE HELP ME!!!!! I don't think I have ever had this problem before.:cry::frown::confused:

uh, it appears you're missing hard drive space, not memory (ram). please use correct terms. it helps to better answer your questons.

---

### Post by taurus on 2008-11-13
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by AZorin on 2008-11-19
I got the problem fixed, I repartitioned the drives (Both my SD card and HDD) and restarted a few times and that fixed it:guitar: The only problem is on the SD card after I copied a folder (around 100-200 MBs)to the card (the card's partition is around 600 MBs(the partition is ext3)) but the space is full can someone plz help?

---

