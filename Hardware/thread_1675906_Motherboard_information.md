---
title: "Motherboard information"
date: 2011-01-26
forum: Hardware
---

### Post by mac4rfree on 2011-01-26
Hi,

I tried to get the motherboard information. I ran the below command.

```
sudo dmidecode
```

I was able to get the information.. 
I am having lot of information about the Motherboard but which is the motherboard number?

---

### Post by fjgaude on 2011-01-26
Go down from the top to System Information. Then you see Manufacturer: and Product Name. That should do it.

---

### Post by mac4rfree on 2011-01-26
ya i can see that,,,but i want to find the motherboard name.. this wat i found in the file..
> Base Board Information
	Manufacturer: Acer           
	Product Name: Columbia                       
	Version: Rev   

---

### Post by gordintoronto on 2011-01-26
You could also do:
sudo lshw > myconfig.txt
gedit myconfig.txt

I think the information you want is right at the top.

---

### Post by fjgaude on 2011-01-26
> **mac4rfree said:**
> ya i can see that,,,but i want to find the motherboard name.. this wat i found in the file..

Your MB is named Columbia. Likely there's no more in the header for the MB.

This all that shows for my MB:

Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: H55N-USB3
	Version: x.x
	Serial Number:  

Maybe try **lshw** and see if anything more shows.

---

### Post by gordintoronto on 2011-01-26
> **fjgaude said:**
> Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: H55N-USB3
	Version: x.x
	Serial Number:  

Maybe try **lshw** and see if anything more shows.

So your motherboard is a Gigabyte H55N-USB3. If you log on to Newegg, you can get the full specs.

---

### Post by fjgaude on 2011-01-26
> **gordintoronto said:**
> So your motherboard is a Gigabyte H55N-USB3. If you log on to Newegg, you can get the full specs.

I homebuilt my rig, notice my signature.

---

### Post by cascade9 on 2011-01-27
> **mac4rfree said:**
> ya i can see that,,,but i want to find the motherboard name.. this wat i found in the file..

Acer columbia is the motherboard.  

Why do you want to know the motehrbaord model for a laptop? 

> **gordintoronto said:**
> So your motherboard is a Gigabyte H55N-USB3. If you log on to Newegg, you can get the full specs.

Maybe for that board you will, but newegg doesnt list all the specs. Why go to newegg anyway? Gigabyte has a website that works well, and can tell more about the motherboard than newegg in most cases.

---

### Post by mac4rfree on 2011-01-27
yes i want to find the motherboard model ....

---

### Post by cascade9 on 2011-01-27
> **mac4rfree said:**
> yes i want to find the motherboard model ....

You've found it. Acer columbia. 

I'd still like to know why you want it ;)

---

### Post by mac4rfree on 2011-01-30
am trying to install "Snow Leopard" OS using kakewalk... for that i need the Motherboard name...

---

### Post by cascade9 on 2011-01-30
You wont get OSX going on that machine with kakewalk. 

There is a very specific list of motherboards supported. I dont think you would even have a the same chipset as any of those boards.....

---

### Post by mac4rfree on 2011-01-31
Thanks for the information.. tats wat i am trying to do.. one more thing.. whatever motherboard name i have seen have some numbers like Gigabyte EP45-UD3L,Gigabyte EP45T-UD3LR etc.. 

But my motherboard is only Acer Columbia ,,, tats it???

---

### Post by cascade9 on 2011-01-31
Yes, thats it. 

Its a laptop, made by a 'corporate' manufacturer, they tend to not give you much information and quite often the motherboards just given a name, or a semi-random sting of numbers (the numbers of motherbaord manufactuers has some logic, eg- GA-EP45T, uses the intel 'P45' chipset)

---

