# Network-Security-Groups-and-Application-Security-Groups
Plan and implement security for virtual networks student lab

In this lab, you will complete the following exercises:

Exercise 1: Create the virtual networking infrastructure

Exercise 2: Deploy virtual machines and test the network filters

### 1️⃣ **Create the virtual networking infrastructure**

Task 1: Create a virtual network

1. Sign-in to the Azure portal https://portal.azure.com/

2. In the Azure portal, in the Search resources, services, and docs text box at the top of the Azure portal page, type Virtual networks and press the Enter key.

<img width="547" height="43" alt="image" src="https://github.com/user-attachments/assets/bdbfcbcc-6fb0-43f2-9dc2-e0975eae2c5d" />

3. On the Virtual networks blade, click + Create.

4. On the Basics tab of the Create virtual network blade, specify the following settings (leave others with their default values) and click Next: IP Addresses:

<img width="863" height="934" alt="image" src="https://github.com/user-attachments/assets/87e879d0-cf91-4147-8e16-2328733fd1e5" />

5. On the IP addresses tab of the Create virtual network blade, set the IPv4 address space to 10.0.0.0/16, and, if needed, in the Subnet name column, click default, on the Edit subnet blade, specify the following settings and click Save:

<img width="1920" height="937" alt="image" src="https://github.com/user-attachments/assets/22bc2ee4-3d49-4171-8b9a-3d1b2cd4eec4" />

6. Back on the IP addresses tab of the Create virtual network blade, click Review + create.

7. On the Review + create tab of the Create virtual network blade, click Create.

Task 2: Create application security groups

1. In the Azure portal, in the Search resources, services, and docs text box at the top of the Azure portal page, type Application security groups and press the Enter key.

2. On the Application security groups blade, click + Create.

3. On the Basics tab of the Create an application security group blade, specify the following settings:

<img width="848" height="532" alt="image" src="https://github.com/user-attachments/assets/a911104f-00c6-4ee7-9768-d9ea4b22100f" />

4. Click Review + create and then click Create. (This group will be for the web servers)

5. Navigate back to the Application security groups blade and click + Create.

6. On the Basics tab of the Create an application security group blade, specify the following settings:

<img width="819" height="637" alt="image" src="https://github.com/user-attachments/assets/c54233f1-f727-4e8c-b08b-e0e3c49632b2" />

7. Click Review + create and then click Create. (This group will be for the management servers)

Task 3: Create a network security group and associate the NSG to the subnet

1. In the Azure portal, in the Search resources, services, and docs text box at the top of the Azure portal page, type Network security groups and press the Enter key.

2. On the Network security groups blade, click + Create.

3. On the Basics tab of the Create network security group blade, specify the following settings:

<img width="838" height="609" alt="image" src="https://github.com/user-attachments/assets/f1006c31-cb02-41de-8775-95b751a130c9" />

4. Click Review + create and then click Create.

5. In the Azure portal, navigate back to the Network security groups blade and click the myNsg entry.

6. On the myNsg blade, in the Settings section, click Subnets and then click + Associate.

7. On the Associate subnet blade, specify the following settings and click OK:

<img width="1717" height="935" alt="image" src="https://github.com/user-attachments/assets/d1fb0181-2810-418e-81b7-5e9950de27b0" />

Task 4: Create inbound NSG security rules to all traffic to web servers and RDP to the servers.

1. On the myNsg blade, in the Settings section, click Inbound security rules.

2. Review the default inbound security rules and then click + Add.

3. On the Add inbound security rule blade, specify the following settings to allow TCP ports 80 and 443 to the myAsgWebServers application security group (leave all other values with their default values):

<img width="1919" height="897" alt="image" src="https://github.com/user-attachments/assets/e03ae314-42a2-4f9c-a165-b38fb9ee106e" />

4. On the Add inbound security rule blade, click Add to create the new inbound rule.

5. On the myNsg blade, in the Settings section, click Inbound security rules, and then click + Add.

6. On the Add inbound security rule blade, specify the following settings to allow the RDP port (TCP 3389) to the myAsgMgmtServers application security group (leave all other values with their default values):

<img width="1919" height="888" alt="image" src="https://github.com/user-attachments/assets/5cf5fd35-15fb-49e0-bc0c-450429d9061e" />

Result: You have deployed a virtual network, network security with inbound security rules, and two application security groups.

### 2️⃣ **Deploy virtual machines and test network filters**

Task 1: Create a virtual machine to use as a web server.

1. In the Azure portal, in the Search resources, services, and docs text box at the top of the Azure portal page, type Virtual machines and press the Enter key.

2. On the Virtual machines blade, click + Create and, in the dropdown list, click + Azure virtual machine.

3. On the Basics tab of the Create a virtual machine blade, specify the following settings (leave others with their default values):

<img width="895" height="663" alt="image" src="https://github.com/user-attachments/assets/60f066ce-f12a-480b-8b71-2353edaf3646" />
<img width="858" height="562" alt="image" src="https://github.com/user-attachments/assets/a6a7c35a-cce0-47ab-9937-7585737889c0" />

(Please create your own password and record it for future reference in subsequent labs)

For public inbound ports, we will rely on the precreated NSG.

4. Click Next: Disks > and, on the Disks tab of the Create a virtual machine blade, set the OS disk type to Standard HDD and click Next: Networking >.

5. On the Networking tab of the Create a virtual machine blade, select the previously created network myVirtualNetwork.

6. Under NIC network security group select None.

7. Click Next: Management >, then click Next: Monitoring >. On the Monitoring tab of the Create a virtual machine blade, verify the following setting:

<img width="713" height="690" alt="image" src="https://github.com/user-attachments/assets/4bc87deb-b1b3-417d-b169-caa69e4e05a6" />

8. Click Review + create, on the Review + create blade, ensure that validation was successful and click Create.

Task 2: Create a virtual machine to use as a management server.

1. In the Azure portal, navigate back to the Virtual machines blade, click + Create, and, in the dropdown list, click + Azure virtual machine.

2. On the Basics tab of the Create a virtual machine blade, specify the following settings (leave others with their default values):

<img width="872" height="644" alt="image" src="https://github.com/user-attachments/assets/7102e87f-0247-45d1-b72a-0d129482410d" />
<img width="912" height="478" alt="image" src="https://github.com/user-attachments/assets/05cf74b6-b5c5-4182-9263-3e9aaf2ac217" />

(Use same password from Virtual Machine Web Server that was just created in the last task)

For public inbound ports, we will rely on the precreated NSG.

3. Click Next: Disks > and, on the Disks tab of the Create a virtual machine blade, set the OS disk type to Standard HDD and click Next: Networking >.

4. On the Networking tab of the Create a virtual machine blade, select the previously created network myVirtualNetwork.

5. Under NIC network security group select None.

6. Click Next: Management >, then click Next: Monitoring >. On the Monitoring tab of the Create a virtual machine blade, verify the following setting:

<img width="707" height="543" alt="image" src="https://github.com/user-attachments/assets/8ae863d4-a0f0-4292-8cdd-70adf26bad59" />

7. Click Review + create, on the Review + create blade, ensure that validation was successful and click Create.

(Wait for both virtual machines to be provisioned before continuing)

Task 3: Associate each virtual machines network interface to its application security group.

1. In the Azure portal, navigate back to the Virtual machines blade and verify that both virtual machines are listed with the Running status.

2. In the list of virtual machines, click the myVMWeb entry.

3. On the myVMWeb blade, in the Networking section, click Network settings and then, on the myVMWeb | Networking settings blade, click the Application security groups tab.

4. Click + Add application security groups, in the Application security group list, select myAsgWebServers, and then click Save.

5. Navigate back to the Virtual machines blade and in the list of virtual machines, click the myVMMgmt entry.

6. On the myVMMgmt blade, in the Networking section, click Networking settings and then, on the myVMMgmt | Networking settings blade, click the Application security groups tab.

7. Click + Add application security groups, in the Application security group list, select myAsgMgmtServers, and then click Save.

Task 4: Test the network traffic filtering

1. Navigate back to the myVMMgmt virtual machine blade.

2. On the myVMMgmt Overview blade, click Connect and, in the drop down menu, click Connect.

3. Download the RDP file and use it to connect to the myVMMgmt Azure VM via Remote Desktop. When prompted to authenticate, provide the following credentials:

<img width="509" height="359" alt="image" src="https://github.com/user-attachments/assets/3d2d7453-c1bc-45c9-acf8-01e5af345bf8" />
(Please use password you have set up for the virtual machines)

Verify that the Remote Desktop connection was successful. At this point you have confirmed you can connect via Remote Desktop to myVMMgmt.

4. In the Azure portal, navigate to the myVMWeb virtual machine blade.

5. On the myVMWeb blade, in the Operations section, click Run command and then click RunPowerShellScript.

6. On the Run Command Script pane, run the following to install the Web server role on myVmWeb:

<img width="852" height="431" alt="image" src="https://github.com/user-attachments/assets/23d8df23-d55a-4927-b17d-4e428e0bd225" />

Wait for the installation to complete. This might take a couple of minutes. At that point, you can verify that myVMWeb can be accessed via HTTP/HTTPS.

7. In the Azure portal, navigate back to the myVMWeb blade.

8. On the myVMWeb blade, identify the Public IP address of the myVmWeb Azure VM.

9. Open another browser tab and navigate to IP address you identified in the previous step.

(The browser page should display the default IIS welcome page because port 80 is allowed inbound from the internet based on the setting of the myAsgWebServers application security group. The network interface of the myVMWeb Azure VM is associated with that application security group.)

Result: You have validated that the NSG and ASG configuration is working and traffic is being correctly managed

<img width="1919" height="1051" alt="image" src="https://github.com/user-attachments/assets/98cf1a1b-5958-4d37-83b4-808176c15b95" />

CLOSING: CLEAN UP RESOURCES
  (Remember to remove any newly created Azure resources that you no longer use. Removing unused resources ensures you will not incur unexpected costs.)

  1. Open the Cloud Shell by clicking the first icon in the top right of the Azure Portal. If prompted, select PowerShell and Create storage.

  2. Ensure PowerShell is selected in the drop-down menu in the upper-left corner of the Cloud Shell pane.

  3. In the PowerShell session within the Cloud Shell pane, run the following to remove the resource group you created in this lab:

<img width="523" height="27" alt="image" src="https://github.com/user-attachments/assets/419dde41-2862-452e-91ff-e8adf67a586e" />
 
  4. Close the Cloud Shell pane.

