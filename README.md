foreman-ansible
===============

An Ansible ENC (external node classifier) to get, group and classify nodes based on the Puppet facts in The Foreman.

This project is for you if you use Foreman (http://theforeman.org/) and Puppet (https://puppetlabs.com) to handle your configuration management (and possibly provisioning) and you want to make use of the the Puppet facts in Foreman to drive the excellent config management/deployment/orchestration tool Ansible (http://ansible.cc/).
* How it works:
The Foreman provides an excellent api which allows you get lists of nodes based on certain "facts" about the nodes. We make use of this, and Ansible's ability to drop in new ENC's,  to get lists of nodes based on specified criteria. This allows us to group and classify your nodes based on any puppet fact.

In foreman-ansible we handle the grouping of nodes in a simple groups.yml YAML file. To group your nodes in another way, simply add another stanza in the groups.yml for the grouping you'd like. I've included a sample groups.yml file.

* How to get it to work:

   * Install the requests python library (http://docs.python-requests.org/en/latest/)
       * Usually 'pip install requests' will do.
   * git clone https://github.com/romeotheriault/foreman-ansible.git
   * chmod +x hosts
   * vim hosts (and change the url variable to point to your foreman instance, and input a valid username and password)
   * vim groups.yml (and change any of the groupnames and search queries to suit your needs)
   * Test it out with ./hosts --list and ./hosts --host <nodename-you-have-in-puppet>
   * Point ansible at it with '-i /path/to/hosts/file' or move it and groups.yml file to /etc/ansible/ at it and fire away.


* Still to do:

    * Make code more robust
    * Add the ability to return children groups
    * Probably more

Pull requests welcome if others find this useful.
