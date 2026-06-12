---
title: "ubuntu 14.04.2 - what nvidia drivers for CUDA"
date: 2015-03-07
forum: Hardware
---

### Post by gasior.tt on 2015-03-07
Hi, after installing cuda toolkit and cuda samples via runfile installation (nvidia driver installed separately - NVIDIA binary driver - version 340.76 from nvidia-340 (open source)))

after running ./deviceQuery i have this:

```
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

cudaGetDeviceCount returned 30
-> unknown error
Result = FAIL


```

nvidia-smi gives me this:
```
+------------------------------------------------------+                       
| NVIDIA-SMI 340.76     Driver Version: 340.76         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 780 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 37%   35C    P8    N/A /  N/A |    287MiB /  3071MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
```

So the question is which nvidia driver will satisfy CUDA set? 

As far as I know there is no xordg/edgers nvidia drivers for ubuntu 14.04.2 ?

?

---

