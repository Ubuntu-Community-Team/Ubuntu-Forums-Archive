---
title: "Apt-mirror won't finish"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by slick666 on 2009-11-03
Like the title says I have apt mirror setup and it won't complete. I have 1.6 gigs left. I ended up putting the command in a loop to see if persistence would get it done.

```

for ((c=0; c<1000; c++))
do
echo The iteration is $c
apt-mirror
done
```

This script has repeated 50 time and not one file has completed. Here's the output
```
The itteration is 53
Downloading 648 index files using 1 threads...
Begin time: Tue Nov  3 07:25:15 2009
[1]... [0]... 
End time: Tue Nov  3 07:26:19 2009

Proceed indexes: [PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP]

1.6 GiB will be downloaded into archive.
Downloading 1196 archive files using 1 threads...
Begin time: Tue Nov  3 07:27:14 2009
[1]... 

```

My internet can be a little choppy but I would think that the file would eventually complete.

My gateway is showing a throughput of 650 Kbps to 1.3 Mbps. Any advice is appreciated.

---

