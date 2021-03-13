# ping-setup---allow-or-block


 Create a Setup so that you can ping google but not able to ping Facebook from same system.

What is a routing table and how does it work?
A routing table contains the information necessary to forward a packet along the best path toward its destination. Each packet contains information about its origin and destination.
Routing Table provides the device with instructions for sending the packet to the next hop on its route across the network.
What does a netmask do?
A Netmask is a 32-bit “mask” used to divide an IP address into subnets and specify the network’s available hosts. In a netmask, two bits are always automatically assigned.
For example, in 255.255. 225.0, “0” is the assigned network address.
What is meant by default gateway?
The default gateway is the path used to pass information when the device doesn’t know where the destination is. More directly, a default gateway is a router that connects your host to remote network segments.
It’s the exit point for all the packets in your network that have destinations outside your network.
What is the use of Route command in Linux?
route command in Linux is used when you want to work with the IP/kernel routing table. It is mainly used to set up static routes to specific hosts or networks via an interface.
It is used for showing or update the IP/kernel routing table.
What is IP address ?
An IP address is a string of numbers separated by periods. IP addresses are expressed as a set of four numbers — an example address might be 192.158. 1.38. Each number in the set can range from 0 to 255.
So lets jump to our practical part……
so we can run following commands:-
# route -n

Now we can see we are able to ping to google.com and www.facebook.com or not..
# ping -4 www.google.com
# ping -4 www.facebook.com

Now we can create one text file where we can put all the information of our ip’s which we have to be used in future.
so for this we can use cat command.
# cat > ping.txt
gw 192.168.1.1
google_ip 172.217.166.36
facebook_ip 69.171.250.35

Now we have to delete the default gateway.
# route del -net 0.0.0.0
# route -n

Here, After deleting the default gateway we have to be check we are able to www.ping google.com and www.facebook.com or not.

Now, we have to be create the rule for routing table.
# route add -net 172.217.166.0/24 gw 192.168.1.1 enp0s3

So, Here we have to check now we are able to ping to www.google.com or not.
# ping www.google.com
We also check we are not able to ping to facebook.
# ping www.facebook.com

Now we can also go to mozilla firefox and check we are able to see the page of www.google.com or not.

And also check here we are not able to open www.facebook.com.
