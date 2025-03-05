# React OTP Input

A customizable OTP (One-Time Password) input component for React applications with TypeScript support.

## Features

- TypeScript support
- Customizable length
- Keyboard navigation
- Paste support
- Mobile-friendly numeric input
- Accessible
- Customizable styling
- Disabled state support
- Secure input mode
- Form library integration (react-hook-form, Formik, etc.)

## Installation

```bash
npm install react-otp-input
# or
yarn add react-otp-input
```

## Usage

```tsx
import { OtpInput } from 'react-otp-input';

function App() {
  const handleComplete = (value: string) => {
    console.log('OTP completed:', value);
  };

  return (
    <OtpInput
      length={6}
      onComplete={handleComplete}
      onChange={(value) => console.log('Current value:', value)}
      placeholder="○"
      disabled={false}
      style={{ margin: '20px' }}
      inputStyle={{ borderColor: '#000' }}
    />
  );
}
```

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| length | number | 4 | Number of input fields |
| onChange | (value: string) => void | - | Callback when value changes |
| onComplete | (value: string) => void | - | Callback when all fields are filled |
| disabled | boolean | false | Disable the input fields |
| placeholder | string | "○" | Placeholder character |
| inputMode | "numeric" \| "tel" | "numeric" | Input mode for mobile devices |
| style | React.CSSProperties | - | Container style |
| inputStyle | React.CSSProperties | - | Individual input style |
| secure | boolean | false | Hide input values |
| maskChar | string | "•" | Character to use for masking |
| value | string | - | Controlled input value |
| defaultValue | string | "" | Default input value |

## Form Integration

### React Hook Form

```tsx
import { useForm, Controller } from 'react-hook-form';
import { OtpInput } from 'react-otp-input';

function Form() {
  const { control, handleSubmit } = useForm({
    defaultValues: {
      otp: ''
    }
  });

  const onSubmit = (data: { otp: string }) => {
    console.log('OTP:', data.otp);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Controller
        name="otp"
        control={control}
        rules={{ required: true, minLength: 4 }}
        render={({ field }) => (
          <OtpInput
            length={4}
            value={field.value}
            onChange={field.onChange}
            ref={field.ref}
          />
        )}
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

## Development

```bash
# Install dependencies
npm install

# Start Storybook
npm run storybook

# Build
npm run build

# Run tests
npm test
```

## License

MIT 