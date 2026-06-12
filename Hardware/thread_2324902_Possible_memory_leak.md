---
title: "Possible memory leak?"
date: 2016-05-17
forum: Hardware
---

### Post by sacherus on 2016-05-17
Hi guys,
I'm not sure is it good place to put this thread, but I have "computing server" which I'm using for CUDA computation (with some framework). After a some computation and killing all computing processes I get 6.7GB/32GB free memory. After some point I'm not able to make anything that needs more memory. Any ideas?

free:
```

             total       used       free     shared    buffers     cached
Mem:           31G        25G       5.7G        73M        26M       983M
-/+ buffers/cache:        24G       6.7G
Swap:           0B         0B         0B

```

ps_mem.py:
```

(...)
 12.9 MiB +   1.8 MiB =  14.7 MiB       bash (4)
 14.9 MiB +  16.2 MiB =  31.0 MiB       systemd-journald
---------------------------------
                        119.5 MiB



```


After restart:
```

             total       used       free     shared    buffers     cached
Mem:           31G       463M        30G       9.6M        33M       210M
-/+ buffers/cache:       218M        31G
Swap:           0B         0B         0B

```

```

(...)
  8.4 MiB +  70.0 KiB =   8.4 MiB       dhclient
  8.0 MiB +   1.8 MiB =   9.8 MiB       NetworkManager
---------------------------------
                         88.3 MiB

```

---

