---
title: "Huge gpu problem"
date: 2022-11-27
forum: Hardware
---

### Post by devdlp on 2022-11-27
My 1060 nvidia gpu isnt being recognized or something on ubuntu 22.0.4 with any driver for some reason.
i did something wrong i think i know whatc it is.
i found this becuase i wanted cool-bits working for overclocking 
"sudo nvidia-xconfig -a --cool-bits=16 --allow-empty-initial-configuration"
that may be the problem greenwithenvy isnt working. im not toatlly sure.
looking for some help beuace i cant do my normal things on it right now but i know the gpu is being seen sense theres three monitorsa here two of which is plugged in the back of it.
all three are on but things are telling my im using intel graphics so im lost right now.
i know its late but i need help with this. Any ideas would help, and thanks.

---

### Post by devdlp on 2022-11-27
It was not possible to find the NVIDI NV-CONTROL X extension on the current Display device. Please make sure that the NVIDIA proprietary display drivers are installed and they support your current GPU. What can be done to fix this issue now?

---

### Post by devdlp on 2022-11-27
FIXED!!! simply becuase i was on wayland.
so i moved to ubuntu then updated flatpak and nvidia drivers! bang done!

---

