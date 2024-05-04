In this document I am gonna be writting how this project was created and my step by step process of learning and implementing the application.


Step 1  - Created a next application 
	npx create-next-app@latest

Step 2  - Configure the project like this 
	typescript  	- yes
	ESLint 			- yes
	tailwindCss 	- yes
	src/directory	- yes
	name the project any thing in small case 

Step 3  - src/app folder 
	The src/app/page.tsx is the default landing page of the application 
		It may serve as a template for creating new pages within the application.
		Developers might use it as a starting point when creating new pages to maintain consistency in layout or functionality.
	The src/app/layout.tsx is the overall structure of the application 
		It encapsulates common UI elements such as headers, footers, navigation bars, or sidebars that are shared across multiple pages.
		Developers use this layout component by wrapping it around individual page components to apply a consistent layout to those pages.

	The page.tsx is passed in the layout and then displayed as children inside the layout page.

Step 4  - Remove all the page.tsx content and add dummy content in it. Add few tailwind classes into it to check if the tailwind classes are working properly or not.

Step 5  - Made a component folder in the src/app folder and start making components in the folder.
		Made a lib folder as well and make a new utils.ts file 

Step 6  - Add a ui library named shadcn-ui 
			npx shadcn-ui add accordion
				./src/app/comonents/ui
			yarn add lucide-react  ( for icons )
			yarn add tailwind-merge clsx

Step 7  - In utils.ts export a new function called as cn 
			which allows you to write conditional classes

Step 8  - Now start writing Chat.tsx component and make a box like structure that looks like a chat bot in right bottom
		Use Accordion from shadcn-ui for the box structure.

Step 9  - Now when there is a box like srtructure in the right corner bottom then start filling the box structure and fill content into it,
		that is start making internal components in Chat Component, example ChatHeader etc.

Step 10 - Start making the ChatInput component and place it in Chat Component under the chat header component 
		In the ChatInput component make the component such that
				the component should have an interface 'ChatInputProps' which inherit all the properties of a Html div element 
													syntax - interface ChatInputProps extends HTMLAttributes<HTMLDivElement> 
				what this allows is to allow the ChatInput component accept argumennts that any div elemrnt can accept 
													const ChatInput: FC<ChatInputProps> = ({className, ...props}) => 
				Here in this component we accept the props in a destructured way... we destructure the CSS className property passed to the ChatInput component from the Chat component and the rest props are passed to the props keyword 
				Here the props keyword conains all the other props passed by the chat component

Step 11 - Start the designing of the ChatInput 
		use tailwind libraries like tailwind/forms ( add this to the plugin in tailwind.config.ts) for making the chat bot look good
		also add libraries like textarea autosize  and use its component

Step 12 - Keep track of the state of the input ( useState)
		give the textareaAutosize the value of the input from useState 
		add onChange function on it to change the value of state variable

Step 13 - Add react query to your project
		When the user gives some input to the chat bot it gives the input to the API and then the API gets the generated text 
		the generated text is in a readable stream and to display the readable stream we use react query in the porject. So install react query 
			yarn add @tanstack/react-query 

			Read about react query 
			Add Provider component to the project 
			wrap the layout with Provider component 

		In the reactquery there is a mutation function / useMutation,  which allows you to send an api request to the backend 
		and this also allows you to add onSuccess handlers in the request 
		in the parameters of the mutation function get the message from the user ( access it form the texr area component )
		then send the message to the beackend api, and then return the response body

Step 14 - Add input validaion through zod
		in the lib folder make a new folder named validator and add input validation .
		Define the message schema by z object, then export the MessageArraySchema 

Step 15 - Start designing the backend 
		In the app folder add an api folder and add a message folder 
		in app/api/message add a file name route.ts 

Step 16 - Design the interface of chatGPTMessage 
	 	and the file openai-stream.ts
# ChatBot_ai
