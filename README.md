

<h1> Virtual-SOHO-Router-Mini-Lab-UTM-Windows-11-and Linux Ubuntu </h1>

<h2>Description</h2>
To practice IP configuration, DHCP details and network troubleshooting using UTM's NAT mode to set up a virtual router, creating a SOHO network that is then translated using NAT on my VM. I do the same in Linux and test some networking commands in order to practice troubleshooting networking issues.
<br />


<h2>Utilities Used</h2>

- <b>Command Prompt</b>
- <b>Terminal</b> 


<h2>Environments Used </h2>

- <b>Windows 11</b> (21H2)
- <b>Linux Ubuntu</b>

<h2>Project run through:</h2>

<p align="center">
In order to set up the router I need to ensure the Windows 11 VM is set to Shared Network as this will allow Network Address Translation so I can use the router virtually : <br/>
<img src="https://i.postimg.cc/MphTH4QK/1-setting-VM-to-shared-network.png" height="80%" width="80%" alt="Open command ready drive"/>
<br />
<br />

Starting up Windows 11 vm, I start the command prompt and run the command ipconfig to get some network information. This gives us the default gateway 192.168.64.1 (my router) and IPV4 private address of 192.168.64.2 (my VM) <br/>
<img src="https://i.postimg.cc/y8wdx5Z6/2-verifying-IP-Router-configuration.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


Now to test the routers connection to my VM, I ping 192.168.64.1 which shows a rapid millisecond connection obviously as it is my own router and the connection is good. I also use ping 8.8.8.8 to test the outside internet connection from my router. This shows around 4 hops/packets of data that is my router trying to connect with Google's web server of 8.8.8.8, which shows a max speed of 19 milliseconds, with no packets/hops lost. We have internet connection.  <br/>
<img src="https://i.postimg.cc/x1WC87z1/3-pinging-default-gateway-and-google-server.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

The next networking command I used is Tracert which stands for Trace route. I wanted to use this to find out how long it takes to reach Google's 8.8.8.8 server and how many hops it takes. Each 'hop' is a level 3 network device like a firewall, router or intrusion detection system. There are around 10 with Google. <br/>
<img src="https://i.postimg.cc/FH2RzqLz/4-using-Tracert.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
I also included the pathping command to find out exactly where the problem routers or netwrok devices are on a connection attempt. Bascially combines tracert showing the path and then pinging of each 'hop' inbetween, then displaying diagnostics so you can see where sluggish points may be. 
<img src="https://i.postimg.cc/yNcNZPmY/5-using-Pathping.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

Finally on the Windows VM I just wanted to see all the information so used ipconfig /all. This gives us an overall display of all the virtual SOHO connections and other information  <br/>
<img src="https://i.postimg.cc/JhZhkqN0/6-using-ipconfig-all.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next I switch to my Ubuntu Linux VM and try to do similar networking commands in Terminal to gather more information. Here I used ip addr command to display the VMs address. We can see here under section 2. inet 192.168.4/24 this is my IPV4 private address with the 24 showing CIDR notation and subnet mask. Also under inet6 it shows the longer IPV6 address as our physical home network is configured for IPV6 on Linksys. <br/>
<img src="https://i.postimg.cc/25h5ZwQ5/7-using-ip-addr-in-linux.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Here, like in the windows command prompt, I am just using ping again but obivously in Linux.  <br/>
<img src="https://i.postimg.cc/3wmwvBXd/8-using-ping-in-linux.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now I wanted to find out more about the website www.google.com as an example. So I use the dig command. This functions like nslookup in Windows and begins to query Google's DNS server <br/>
<img src="https://i.postimg.cc/q7y73Ls3/9-dig-www-google-com.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

In this project I wanted to practice some networking commands in my own VM homelab environments. It's useful to start applying these command lines and get used to using them and using the information that's issued back. Good for troubleshooting network connections. If someone was complaining the internet was down or 'not working', I could start by pinging the edge of the SOHO at the routers address first. It might be easier just to skip that and ping a popular high uptime server like Google first, then work back and test your own network connections if Google's works and is up.
