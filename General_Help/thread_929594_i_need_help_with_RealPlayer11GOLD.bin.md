---
title: "i need help with RealPlayer11GOLD.bin"
date: 2008-09-25
forum: General Help
---

### Post by THE BLUE DRAGON on 2008-09-25
hi 
i have donwload RealPlayer11GOLD.bin from
[http://www.real.com/linux](http://www.real.com/linux)
and i install it by this way 

1. Open your Terminal

2. Change to the directory that the .bin was downloaded to. example:
Code:

cd home 
cd dragon

3. To make sure you are in the same directory as your .bin type

ls

That will display the files in your current directory.

4. Now that you are in the appropriate directory, type sudo chmod +x RealPlayer11GOLD.bin That changes your bin to an executable file.

5. Finally, type ./RealPlayer11GOLD.bin to run it.

ok then the install complet but when i open it 
it`s give me error 
Could not launch menu item
Failed to execute child process "realplay" (No such file or directory)

---

### Post by eggdeng on 2008-09-25
Run
```
sudo updatedb
```
then
```
locate realplay
```
This should tell you the path to the realplay file. Then run it from a terminal as 
```
/path_to_file/realplay
```

---

### Post by THE BLUE DRAGON on 2008-09-25
thanks it`s work now

---

### Post by xiyang81 on 2008-12-04
> **eggdeng said:**
> Run
```
sudo updatedb
```
then
```
locate realplay
```
This should tell you the path to the realplay file. Then run it from a terminal as 
```
/path_to_file/realplay
```
thankyou! I have done as you say. I'm OK now.

---

