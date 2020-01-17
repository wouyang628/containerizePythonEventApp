# containerizePythonEventApp
containerize the event_consumer.py and remediation.py

To build the image:
```
docker build --tag edi .
```
start the docker
```
docker run --name edi edi  
```
stop and remove the docker
```
docker rm edi
docker rmi edi
```

generate an event and check the container is running correctly:
```
[jcluser@centos ~]$ docker run --name edi edi
started..............

{'device-id': 'vMX-1', 'group': 'all', 'group-type': 'device', 'keys': {'_instance_id': '["interface_status"]', '_playbook_name': 'interface_status', 'element_name': 'ge-0/0/2'}, 'message': 'ge-0/0/2 admin state DOWN', 'rule': 'interface_status', 'severity': 'major', 'topic': 'external', 'trigger': 'interface_down'}
application name:healthbot
print event.message
{'device_ID': 'vMX-1', 'device_type': 'network', 'timestamp': '2020-01-17 14:50:37', 'vendor': 'na', 'element_name': 'ge-0/0/2', 'error_code': 'interface_down', 'error_message': 'ge-0/0/2 admin state DOWN', 'status': 'new', 'action': 'none', 'source': 'healthbot', 'result': 'none'}
saved to Elastic
```
