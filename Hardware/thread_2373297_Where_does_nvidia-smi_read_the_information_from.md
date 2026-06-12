---
title: "Where does nvidia-smi read the information from ?"
date: 2017-10-04
forum: Hardware
---

### Post by bp1234 on 2017-10-04
Can anyone pls tell me which file does nvidia-smi load its output from. It shows the gpu name and number of gpus but where does it get this info from.
Is there any specific file it relies on ?

---

### Post by Yellow Pasque on 2017-10-05
I don't think it reads from a file. It queries the hardware directly using: [https://developer.nvidia.com/nvidia-management-library-nvml](https://developer.nvidia.com/nvidia-management-library-nvml)
In other words, nvidia-smi is a backend tool that could be used to write an informational file, rather than just a frontend tool to read a file and produce output aimed at human readability.

---

