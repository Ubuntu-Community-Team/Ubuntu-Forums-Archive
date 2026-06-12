---
title: "[SOLVED]System freezes or start up to black screens,broke Display Drivers,"
date: 2010-08-30
forum: Hardware
---

### Post by shakethenation on 2010-08-30
I was experiencing this and i run ubuntu 10.04 LTS on an ASUS 64 bit  laptop with a ATI Mobility Radeon HD 5870 Graphics Chip.  Caused windows  to freeze up at start up too.  Finally found it is major issues with  the compatibility of the ATI display drivers and misconfigurations  between xorg and fglrx.

These are the steps you take to solve this issue: 

1.) Check proper installation of kernal headers with

    ```
sudo apt-get install linux-headers-$(uname -r)
```2.)Install the fglrx driver

    ```
sudo apt-get install fglrx
```3.)Select fglrx to use, selection for me was 0

    ```
sudo update-alternatives --config gl_conf
```4.)Then:

    ```
sudo ldconfig
```    ```
sudo update-initramfs -u
```config xorg

    ```
sudo aticonfig --initial
```And that fixed it for me. Hope it helps for you too!!!

---

### Post by tanpopo_chan on 2011-03-16
Brilliant!

Thank you!!

---

