---
title: "Building a Supercomputer, seeking hardware advice"
date: 2014-04-28
forum: Hardware
---

### Post by keuller on 2014-04-28
Hi,

I am a graduate student that was just awarded $20,000 to build my next "supercomputer."

My first build was a simple affair with five cheap mobo's with cheap quad-core cpu's and 4GB of RAM on Ubuntu 10.04 that works on a Plasma Fusion simulation that involves 10's of thousands of particles.

This next build will be quite a bit more robust, and I would like some advice regarding my hardware choices. Specifically the power handling and whether the components I've got will "play nice" with Ubuntu. As much as possible I am hoping to hit the ground running with the OS but I'm sure there will be tons of issues running brand new GPU's.

New Build:
5x Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811147155](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147155)
5x Mobo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813182322](http://www.newegg.com/Product/Product.aspx?Item=N82E16813182322)
10x GPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814202094](http://www.newegg.com/Product/Product.aspx?Item=N82E16814202094)
10x CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113304](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113304)
5x PSU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817182251](http://www.newegg.com/Product/Product.aspx?Item=N82E16817182251)
10x RAM: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820239657](http://www.newegg.com/Product/Product.aspx?Item=N82E16820239657)
10x CPU Cooler: [http://www.newegg.com/Product/Product.aspx?Item=N82E16835114137](http://www.newegg.com/Product/Product.aspx?Item=N82E16835114137)
3x SSD: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820148693](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148693)

Notes:
1. The GPU's will not be running in Crossfire. We are utilizing them for computation power only. The simulation is very simple; we are moving particles around and calculating interactions, then moving all the particles again.

2. Our simulation is a resource hog. When we hit "go" on our current system every cpu is maxed out and every thread is being utilized. I only mention this because when we find the maximum threshold of this thing, we will be (hopefully) utilizing every single core across those GPU's and we don't want to burn up our power supplies.

3. This will be mounted in an air conditioned server room with plenty of power in that regard.

4. There are only 3 SSD's because the nodes will have their image pushed to RAM from a "mother-node" when we reboot them. That way we can just roll the image out across all nodes at once when we make a change.


So what do you think? Is this crazy? Am I wasting money on the Mobo and CPU's? I realize the AMD 7990 is pretty new, so has anyone had any success running one (or two :p) with different Ubuntu builds?

Thanks for any advice!

---

