<b>Communication Contract for ranword.py</b>

<b>Dependencies:</b>
<br>import pika
<br>import uuid


<b>Example call:</b>

    def call(self):
        self.response = None
        self.corr_id = str(uuid.uuid4())
        self.channel.basic_publish(
            exchange='',
            routing_key='msgbox',
            properties=pika.BasicProperties(
                reply_to=self.callback_queue,
                correlation_id=self.corr_id,
            ),
            body='')
        self.connection.process_data_events(time_limit=None)
        return self.response
        
  wordgen = ClientClassName()
  <br>response = wordgen.call()

  
  *ClientClassName is a placeholder for the class name in client program.
  
  
<b>Sequence Diagram:</b>
![UMLseqdiagram](https://user-images.githubusercontent.com/102643404/219220146-3294bc8f-6b1e-4141-9c89-480c4037f982.jpg)

